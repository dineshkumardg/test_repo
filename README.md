# Timesheet Management System
	
A web based employee timesheet managmenet system.

## Key Features

*	Dashboard: When a user logs he can view his submitted timesheets in the dashboard. From the dashboard users can navigate to other pages.

*	Submit timesheet: Only the timesheet submitter is allowed to submit the timesheets. The “submit timesheets” link is visible when clicked on “Home”

*	Approve/Reject timesheet: The users who is manager/GM/FM/GFM can view the list of timesheets needs their approval by clicking “Approvable Timesheet”.

* View timesheet log: Click on the timesheet id to view the timesheet approval history.


Note:Currently only the timesheet submitter can submit timesheets for Employees. Employee submitting his own timesheets is in process.

## Design

The current folder structure for this project is

	rez-eams
	├── eams
	│   ├── core
	│   │   └── fixtures
	│   │   └── migrations
	│   │   └── admin
	│   │   └── views
	│   │   └── tests
	│   │   └── tables
	│   │   └── models
	│   │   └── forms
	│   │   └── constants
	│   │   └── fields
	│   │   └── urls
	│   │   └── helpers
	│   ├── static
	│   │   ├── css
	│   │   ├── images
	│   │   └── js
	│   └── templates
	│   │   ├── timsheet
	│   │   ├── base
	├── docs
	│   ├── diagrams
	│   ├── static
	├── scripts
	    ├── reset
	    ├── sample_data
	
An initial sequence diagram:

![Sequence Diagram](docs/static/sequence.mmd.png)

The above graph is based on this [definition](docs/diagrams/sequence.mmd) which is written in [mermaid](https://knsv.github.io/mermaid/#mermaid-cli) syntax.

## Process

For the prototype we have used the Rezgroup-Ritcco architecture. We have used the following employee organisational relation for the implementation.

Role description:
	
1. Entry Level – The employee in a company. He can only view the list of timesheets submitted for him in the dashboard and its log.
2. Timesheet Submitter – The person who submits timesheet for all employees in a business unit and all its child business unit where he plays the role.
3. Manager – The employee who is a manager in a business unit. He can approve/reject all the timesheet which are for his approval. He can view and approve/reject only the timesheet of the business unit where he plays the manager role. The current state of the timesheet for a manager approval will be either new or resubmit.
4. Finance Manager – The employee who is a finance manager in a business unit. He can approve/reject all the timesheet which are for his approval. He can view and approve/reject the timesheet of the business unit where he plays the finance manager role and also its child business units. The current state of the timesheet for a finance manager approval will be manager_approved.
5. General Manager – The employee who is a general manager for business units. He can approve/reject all the timesheet which are for his approval. He can view and approve/reject the timesheet of the business units where he plays the general manager role and also its child business units. The current state of the timesheet for a finance manager approval will be fm_approved.
6. Group Finance Manager – The employee who is a general manager for business units. He can approve/reject all the timesheet which are for his approval. He can view and approve/reject the timesheet of the business units where he plays the general manager role and also its child business units. The current state of the timesheet for a group finance manager approval will be gm_approved.

Notes:

When a timesheet is submitted by timsheet submitter for a user
	
1. It shows up in the corresponding users dashboard it will also shows up in the corresponding users business unit 's manager approval dashboard 
	
2. When a timesheet is submitted for a manager it also will be send to the manager approvals
	
3. When a timesheet is submitted fot GM,FM,GFM the manager approval is skipped and they are directly send to FM's approval with the current state being manager_approved
	
4. The manager, FM, GM and GFM at any time edit the timesheet which are there in the approval dashbpard.

## How to run

* create a virtual env: virtualenv -p python3 eams
* source ~/eams/bin/activate
* cd to project directory
* The app assumes that the postgresql username is 'postgres' and password is 'password' if the password is different you can either change the settings.py to your local postgres password or change the password with the following commands.

      sudo -u postgres psql; 
      ALTER USER postgres with password 'password';
* Run reset.py
      python3 scripts/reset.py(python3 in virtualenv created)
  If everything works fine, the script will start the server at http://localhost:8000/






