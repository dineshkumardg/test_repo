# Timesheet Management System
	
A web based employee timesheet managmenet system.

## Key Features

*	Dashboard: When a user logs he can view his submitted timesheets in the dashboard. From the dashboard users can navigate to other pages.

*	Submit timesheet: Only the timesheet submitter is allowed to submit the timesheets. The “submit timesheets” link is visible when clicked on “Home”

*	Approve/Reject timesheet: The users who is manager/GM/FM/GFM can view the list of timesheets needs their approval by clicking “Approvable Timesheet”.

* View timesheet log: Click on the timesheet id to view the timesheet approval history.


Note:Currently only the timesheet submitter can submit timesheets for Employees. Employee submitting his own timesheets is in process.

 The app assumes that the postgresql username is 'postgres' and password is 'password' if the password is different you can either change the settings.py to your local postgres password or change the password with the following commands.

      sudo -u postgres psql; 
      ALTER USER postgres with password 'password';
* Run reset.py
      python3 scripts/reset.py(python3 in virtualenv created)
  If everything works fine, the script will start the server at http://localhost:8000/






