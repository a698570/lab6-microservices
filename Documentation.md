# Documentation

First, we start the `Registration` server that runs Eureka, which waits for services to register:

![](img/00_Eureka_terminal_init.png)

Then we start the `Accounts` server, that notifies `Registration` about being in `localhost:2222`:

![](img/01_Accounts_terminal_init.png)

Then we start the `Web` server, that notifies `Registration` about being in `localhost:3333`

![](img/02_Web_terminal_init.png)

We can see at the log of `Registration` how both `Accounts` and `Web` have been registered:

![](img/03_Eureka_terminal_registered.png)

And they are also visible at the dashboard of Eureka:

![](img/04_Eureka_dashboard_registered.png)

Then we start another `Accounts` server, that notifies `Registration` about being in `localhost:4444`

![](img/05_Account_terminal_init_4444.png)

Which is reflected i the log of `Registration`:

![](img/06_Eureka_terminal_register_4444.png)

And at the dashboard:

![](img/07_Eureka_dashboard_registered_4444.png)

When searching an account through the `Web` interface, it uses the `Accounts` server at 4444:

![](img/08_Web_terminal_search.png)

Here is the log of the 4444 `Accounts` server:

![](img/09_Account_terminal_search_4444.png)

Then we kill the `Accounts` server at 4444, which is detected by `registration` and displayed at the dashboard:

![](img/10_Eureka_dashboard_kill_4444.png)

Now, when searching again at `Web`, it uses the `Accounts` server at 2222 instead, thanks to Eureka providing it 
with a list of available servers:

![](img/11_Web_terminal_search_2222.png)

As we can see in the logs of `Accounts`:

![](img/12_Account_terminal_search_2222.png)
