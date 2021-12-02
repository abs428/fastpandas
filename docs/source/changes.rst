Miscommunication
================

One common practical issue is that the problem statement that the developer understands is not the problem that has to be solved. Which means that writing code in a way that supports changes in requirements is recommended. One simple way is to use a function with the variables of interest to be passed as inputs to it. This way, if the Company decides that a Wagoner gets to sleep for 12 hours instead of the originally specified 10 hours, it'll be a minor change. It helps to create self contained pieces of code that can be developed and tested independently - the idea is called "abstraction"[#]_.

Other more time consuming issues arise due to miscommunication. After discussion with the Company's representatives, you realize that the definition of the parameter ``work_lim`` is

    The maximum time the Wagoner can spend working per 'day'. A 'full' day looks like waking up at `start`, working for `recess` hours, taking a break that lasts for `short_break` hours, working till he has put in `work_lim` hours of work that day. Then, he goes to sleep.

Please modify the code to adhere to the amended problem statement.

.. [#] `This <https://composingprograms.com/pages/12-elements-of-programming.html>`_ is a good resource to understand abstraction and other important concepts.