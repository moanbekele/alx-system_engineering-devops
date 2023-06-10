#   0x19. Postmortem

An outage happened on a particular Ubuntu 14.04 container that was running an Apache web server, resulting in 500 Internal Server Error responses when the server received GET requests. This incident occurred around 3:00 PM East Africa Time on Saturday, June 10, 2023, which is roughly the same as the GMT+3 time zone in Ethiopia. The server was supposed to return an HTML file that defined a basic Holberton WordPress website. The problem occurred right after ALX's System Engineering & DevOps project 0x19 was released.

<hr>

## Debugging 



1.  Next, they navigated to the `sites-available` directory located at `/etc/apache2/` to determine where the web server was serving content from. They discovered that the server was serving content located in the `/var/www/html/` directory.

2.  To troubleshoot a potential issue, the individual used the `strace` command on the Process ID (PID) of the `root` Apache process in one terminal, while simultaneously using the `curl`` command to access the server in another terminal. However, the `strace` command did not provide any useful information.

3.  The individual repeated the previous step, but this time using the PID of the `www-data` process instead. This time, the `strace` command yielded useful information that indicated an error (-1 ENOENT) when attempting to access the file `/var/www/html/wp-includes/class-wp-locale.phpp`.

4.  To locate the erroneous file extension, the individual proceeded to search through the files in the `/var/www/html/` directory one-by-one using the Vim pattern matching feature. They were able to locate the error in the `wp-settings.php` file, specifically on line 137, where there was a trailing `p` at the end of the file extension (`.phpp`).

5.  To fix the issue, the individual simply removed the trailing `p` from the file extension in the `wp-settings.php` file. They then tested the server once again using the `curl` command and were able to confirm that the error had been resolved (status code 200).

6.  Finally, to automate the process of fixing the error, the individual wrote a Puppet manifest to automatically remove the erroneous file extension in the `wp-settings.php` file.


## Summation

In essence, the problem was caused by a typing mistake- a common issue that can occur when working with code. Specifically, the WordPress application was experiencing a critical error in the `wp-settings.php` file when trying to load the `class-wp-locale.phpp` file, which did not exist. The correct file name was actually `class-wp-locale.php`, and it was located in the `wp-content` directory of the application folder.

To resolve the issue, a simple fix was implemented- the typo was corrected by removing the trailing `p` from the file extension in the `wp-settings.php` file.
<hr>

## Prevention
It is important to note that the recent outage was caused by an application error and not a web server error. To avoid such outages in the future, it is recommended to follow the following guidelines:

*   Firstly, it is crucial to thoroughly test the application before deployment. Multiple rounds of testing should be carried out to catch any potential errors early on. Had the application been thoroughly tested before deployment, the error that caused the outage could have been detected and addressed much earlier.

*   Secondly, it is advisable to enable an uptime-monitoring service like UptimeRobot to keep track of the website`s status. This will help in detecting any outages and alerting the team instantly to take prompt action.

*   In response to the error, a Puppet manifest named 0-strace_is_your_friend.pp was created to automate the fixing of any similar errors that may occur in the future. The manifest replaces any `phpp` extensions in the `wp-settings.php` file located in `/var/www/html/` with `php`.

*   However, it is important to remember that errors can happen even to experienced programmers. Therefore, it is crucial to take the necessary precautions to avoid similar errors in the future, while also being prepared to resolve them quickly and efficiently if they do occur.

