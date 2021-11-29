Getting Started
===============

    Once upon a time, long, long ago, in a land far, far away, in times that were nothing like ours [#]_, there were folk, known to commoners as simply the "Company", that sold expensive bottled water [#]_. People believed that this liquid had some magical, life prolonging properties [#]_.

    The Company transported their wares to every corner of the Empire in wagons. Before embarking on a journey every Wagoner received a schedule [#]_ that looked like the following :-

    .. csv-table:: **Commute durations**
        :header: "Starting from", "Destination", "Duration in hours"
        :widths: 10, 10, 10
        :file: sample_journey.csv
        :align: left

    Wagoners can work for **8 hours** straight before they feel the need to rest. Their work involves both riding and "unloading the goods". Unloading invloves siphoning the precious fluid from the barrels on their wagons to small bottles that can be sold to the fashinable that can afford them. Unloading takes about **2 hours at the destination**. After working for 8 hours, the Wagoner takes a short break lasting **30 minutes**. Then he continues working till he has worked for a total of **14 hours**. At this point, his day ends and he falls asleep, irrespective of where he is [#]_ . His "internal clock" resets after a **10 hour** slumber and he's ready for another 14 hours of work.

    By some arcane means, somebody smart at the Company decided that a Wagoner can visit at most 4 towns in one journey [#]_ . The schedule above is of one such long journey. Journeys that have only one destination were the most common. Note that the unloading time at the last destination in every journey is not considered as work. Unloading time is also not considered for certain destinations even though they are part of a long journey [#]_. A Wagoner starts a new journey at daybreak (5 A.M. sharp) and this particular route 

    For the journey in our example, Wagoner #763 assigned to this route spent his time in the following manner -

    .. csv-table:: **What Wagoner #763 did**
        :header: "Duration in hours", "Activity"
        :widths: 10, 5
        :file: 763.csv
        :align: left
    
    The Company deals with a lot of deliveries every day and it was getting too hard to keep track of every Wagoner's journey until somebody heard of this new fangled form of magic called `"python" <https://www.python.org/>`_. Practitioners of the craft known as "programmers" only need data in the form of a "spreadsheet" as they call it containing the data like -

    .. csv-table:: **What the programmer gets**
        :header-rows: 1
        :file: sample_data.csv
    
    **Translation of the data for humans:** Each record in the dataset refers to a route taken by a Wagoner. :math:`leg_i` where :math:`i \in \{1,2,3,4\}` refers to the duration of the every leg of the journey in hours. If a cell is left blank, that means that the journey has already completed. :math:`flag_i` where :math:`i \in \{1,2,3\}` refers to whether unloading time is considered "work" at that particular destination. Concretely, in the above example, the :math:`0` in the sixth row indicates that unloading time at location #2 is not be considered as work ie:- assume that it takes zero effort and time to perform.

    Assuming that all the Wagoners start at the same time from the warehouse, the Company expects the following output -

    .. csv-table:: **Expected output**
        :widths: 30, 30, 5, 5

        time elasped after departure from warehourse to the departure to the second location for Wagoner on the route #0, time elasped after departure from first location to the departure to the third location for Wagoner on the route #0 , ..., ...
        time elasped after departure from warehourse to the departure to the second location for Wagoner on the route #1, time elasped after departure from first location to the departure to the third location for Wagoner on the route #1 , ..., ...
        ..., ..., ..., ...


.. [#] I'm told that dragons roamed freely in the skies among other ridiculous claims.
.. [#] Or something that was chemically indistinguishable from it at any rate
.. [#] "So does normal water", one young natural philosopher had protested. Poor chap, his death was so sudden. He drowned, I'm told.
.. [#] Which was also accompanied by maps, machetes and other things but these details are irrelevant to the plot, such as it is.
.. [#] I reckon that wagons were quite comfy back in the day. Rumors are that these Wagoners were not quite human. I'm inclined to agree.
.. [#] Something to do with the number of barrels that can fit in a wagon. My correspondent tried to explain the intricacies of the system to me but arithmetic was never my strong suit.
.. [#] Don't ask me why. Some bureaucratic error perhaps? The Wagoners didn't have a problem so why do you?