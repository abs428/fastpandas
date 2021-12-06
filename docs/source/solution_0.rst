Potential solution
==================

The following is a potential solution:-

.. code-block:: python

    import pandas as pd

    def to_timedelta(deltas: pd.Series, start_time: datetime):
        """Helper function that converts the durations returned by
        `get_deltas` to arrival times
        """
        return pd.to_timedelta(deltas,unit= 'hours') + start_time

    def create_plan(
    df: pd.DataFrame,
    start: datetime,
    work_lim: float,
    recess: float,
    long_break: float,
    short_break: float,
    overhead: float
    ) -> pd.DataFrame:
        """
        Parameters
        ----------
        df: pd.DataFrame
            The whole dataframe containing the ride times
            for each leg and flags
        
        start: datetime
            The start time of the journey
        
        work_lim: float
            daily time limit for Wagoner
        
        ...
        
        Returns
        -------
        pd.DataFrame
            A DataFrame containing all the arrival(?)
            times for every leg of journey
        """

        legs = df[["leg_1", "leg_2", "leg_3", "leg_4"]]
        diffs = df[["flag_1", "flag_2", "flag_3"]]
        
        # Getting cumulative sums
        cum_legs = legs.cumsum(axis =1)
        diffarray = diffs.cumsum(axis=1).values
        diffarray = np.hstack([np.zeros(len(diffarray)).reshape(-1,1), diffarray])
        
        def get_deltas(i: int) -> pd.Series:
            """Helper function that gets the journey durations in hours for
            each column i. i in {0,1,2,3}.

            Returns a pandas Series
            """
            day = work_lim + long_break # 24 hours. I'm guessing that this is the intent

            drive_time = cum_legs.iloc[:,i]
            unloading_time = overhead * diffarray[:,i]
            work_time = drive_time + unloading_time

            hours_elapsed = work_time % day # Hours elapsed after completion of n full days
            count_days = work_time // day
            count_short_breaks = count_days + hours_elapsed // recess
            count_sleep_breaks = count_days + hours_elapsed // work_lim
            time_for_breaks = count_short_breaks * short_break
            time_for_sleep = count_sleep_breaks * long_break

            total = (
                        work_time + 
                        time_for_breaks + 
                        time_for_sleep
            )

            return total
        
        # Wrapping it up with a list comprehension
        durations = pd.concat([to_timedelta(get_deltas(i), start) for i in range(4)], axis=1)
        return durations

Questions to answer -
1. Is the solution correct?
2. If the solution is correct, is this the fastest implementation that you can think of?