## What is Scheduling?  
Scheduling a program means scheduling the program to run automatically at a specific time / time interval.  

In windows, use Task Scheduler:  
1. Open Task Scheduler → “Create Basic Task”.  
2. Give it a name (e.g. Run Python Script).  
3. Choose a trigger (e.g. “Daily”, “At startup”, etc.).  
4. Choose Action → Start a Program.  
5. In Program/script, enter the path to Python:  
ex. C:\Users\<YourName>\AppData\Local\Programs\Python\Python312\python.exe  
6. In Add arguments, enter your script path (in this context, script means the program we want to schedule)  
"C:\path\to\your_script.py"  
7. Finish the setup.

In Linux or macOS, use cron scheduler:  
A cron schedule, or cron expression, is a string of characters used in Unix-like operating systems (such as Linux and macOS) to define the timing and frequency of automated tasks, known as cron jobs. It allows users to schedule commands or scripts to run at specific times, dates, or intervals.  
A standard cron expression consists of five fields, representing different units of time:  
minute hour day_of_month month day_of_week  
Each field can contain a number, a range, a list, or a special character:  
Minute (0-59): Specifies the minute of the hour.  
Hour (0-23): Specifies the hour of the day (in 24-hour format).  
Day of the month (1-31): Specifies the day of the month.  
Month (1-12 or Jan-Dec): Specifies the month of the year.  
Day of the week (0-7 or Sun-Sat): Specifies the day of the week (both 0 and 7 can represent Sunday).  
Special Characters:  
- `*` (Asterisk): Represents "every" unit of time. For example, * in the minute field means "every minute."  
- `,` (Comma): Separates a list of values. For example, 1,15,30 in the minute field means "at minutes 1, 15, and 30."  
- `-` (Hyphen): Defines a range of values. For example, 9-17 in the hour field means "hours 9 through 17."  
- `/` (Slash): Specifies step values. For example, */10 in the minute field means "every 10 minutes."
  
Alternatively, there are online or cloud services for scheduling:  
We can host our code on GitHub or a server,  
- GitHub Actions: can run your Python script on a cron schedule.  
- AWS Lambda, Google Cloud Functions, or Azure Functions with a scheduler (like CloudWatch Events).  
- Heroku Scheduler for lightweight web apps.


