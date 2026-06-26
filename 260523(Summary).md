# <font color="#00b0f0">Lesson 1 - 8 Summary</font>

---
## <font color="#00b0f0">Lesson 1</font> Salesforce Fundamentals

#### Salesforce
![](Pasted%20image%2020260522172821.png)
- **Multi-tenant cloud**
	- a single instance of the software, database, and supporing infrastructure serves multiple customers
- **App Launcher**
- **Tabs**
- **Page Layout :** Field, Related List

#### Object
- **Table of Data**
- User object
- Row = Record
- Column = Field
- **Standard objects**
	- Account, Contact, Opportunity, Lead, Campaign, Case, User
	- ![151](Pasted%20image%2020260522173259.png)![223](Pasted%20image%2020260522173334.png)
	- **Object Manager** : fields, page layouts, compact layouts customizations (in Setup : Salesforce backend)
		- handles standard, custom objects
	- **Schema Builder** : objects relationships
- Additional Standard objects
	- Entitlement : SLA
	- Event : Calendar (not frequently used) - record page
	- Quote : Quoatation
	- Pricebook : Various price values, used with opportunities
	- Product : used with opportunities
	- Order : Sales Order
	- Campaign Member : Campaign Target (lead, contact)

#### Sandbox
- production org replica / development, testing, or training
- deploy changes
- ![503](Pasted%20image%2020260522173810.png)
- metadata: Config 설정 데이터
## <font color="#00b0f0">Lesson 2</font> The Big Picture: All Users
#### **The Big Picture**
- ![356](Pasted%20image%2020260522174500.png)
- settings and features affect all users

#### Company settings
- **Company Info** : Name&Address, Primary Contact, Default Locale, Currency Locale, Storage Used, Licenses Available
- **Financial Info** : Fiscal Year, Currencies
- **Support Info** : Business Hours, Holidays

#### Corporate locale settings
- **Locale** : Date&Time Formats, # Formats, Name Order, Addresses, Default Currency
- **Language** : All Text, Online Help
- **Time Zone** : Event Start / End Times, Time in Date / Time Fields
- Company Info ( Defaults ) -> User Record ( Automatic Inheritance ) (Personal)
- Corporate -> User -> Record ( Currency )
	- AppExchange Automation

#### User licenses
- Standard User, Chatter User, Experience Cloud User

#### Activities
- no activities tab, Calendar & Tasks exist
- **Tasks** 
	- **User-created** : To Do, Call Log
	- **System-created** : Email
- **Events**
	- User-scheduled interactions (start - end dates / calendars)
		- Personal calendars

#### Chatter
- **Admins' configuration** : User access, Email notifications, Invitations, Feed tracking
- **Chatter Groups** : private, public, unlisted

#### **Slack**
- automation, knowledge, connections = productivity platform

#### Salesforce mobile
- supports mobile browser environments

#### User
- Salesforce org access
- **Personal** : Name, Alias, Email, Phone/Address, Title
- **Access&Security** : Username, Licenses, Profile, Role, Login History
- **Locale** : Time Zone, Locale, Language, Currency

#### **Security Layers**
- ![494](Pasted%20image%2020260522181332.png)
- Building, Floors, Offices, Cabinets
- MFA (Multi-factor authentication)
- SSO (Single Sign On)
- Profile - Login IP Ranges, Login Hours

#### Health Check
- More Restriction = More Score
## <font color="#00b0f0">Lesson 3</font> Features and Object Access
#### Object access
- the kinds of records (objects) access
- License
- CRED (Create Read Edit Delete) Permissions : types of records
  via Profile, Permission Set, or Permission Set Group
#### Profiles
- one user, one profile
- **Settings** (What users see) : Assigned Apps, Tab Settings, Record Type Assignments, Page Layour Assignments, Field Permissions
- **Permissions** (What users do) : App Permissions, System Permissions, Standard or Custom Object(CRED Settings)
- **Standard** : System Adminstrator, Standard User, Solution Manager, Marketing User, Contract Manager, Minimum Access - Salesforce -> cannot be deleted and permissions cannot be edited
	- Minimum Access - Salesforce : Access Activites, Chatter Internal User, Lighning Console User, and View Help Link permissions
		- least-privilege profile, add more permissions via permission sets and permission set groups, custom profiles' starting point
- login hours & login IP ranges Restriction (login hour, IP range, org-wide trusted IP range, autentication)
- **Login hours, Login IP ranges, Record Type & App (defaults), Page Layout Assignment**

#### Permission set
- grants additional permissions to specific users that layer on top of their existing profile
- assign to users from the permission set / user record
- **user's total access = profile + permission sets**
- **User Permissions (system / App), Object Permissions (CRED), Field Permissions, Tabs, Record Types & Apps (not defaults), Connected App Access, Apex Classes, Visualforce Pages, Gustom Permissions**

#### **Permission set groups**
- allow admins to bundle permission sets together
- **muting permission set** : disable selected permissions

#### Field Access
- Field Level Security : controls viewable & editable fields based on profiles and assigned permission sets (through the field-Object page or the profile)
- Page Layout
- most restrictive field access setting will always apply

#### User Access Policies
- make it easier to streamline the process and make assigning and revoking permissions easier
## <font color="#00b0f0">Lesson 4</font> Record Access
#### Record access
- **Full Access** : view, edit, transfer ownership, change record type, delete, share
  Record ownership (VESTD)
- **Read/Write** : view, edit
- **Read-Only** : view
- No Access
- System Permissions, Record Ownership, Organization Wide Defaults, Roles, Sharing

#### **Admins**
- System Admin, Delegated Admin, Custom Admin
- Modify All Data, View All Data

#### **Queues**
- can act as an owner of records
- **Queue Members** : any public groups, roles, roles + subordinates, users
- a list view is automatically created when a queue is created
- can be used with leads, cases, tasks, or custom objects

#### **Organization-wide defaults**
- ![629](Pasted%20image%2020260526170431.png)
- OWD setup guide : pick the lowest access lvl user
  PRIVATE -> PUBLIC READ-ONLY -> PUBLIC READ/WRITE -> PUBLIC READ/WRITE/TRANSFER (Lead, Case Frequent Transfer)
- **Sharing settings** : Public, Hybrid, Private
- ![](Pasted%20image%2020260526170941.png)
- Default Internal open, Default External Access closed
#### Role Hierarchy
- Users in **higher roles** inherit the special ownership privileges (full access) on all records owned by users in roles below them
- Role hierarchies =/=  org charts
- custom object records do not have to be inherited
- when creating a new role, define the lvl of access an account owner will have to the related records owned by users who are not their subordinates (Contact, Opportunity, Case - OWD set for each object: No Access, View, or Edit dependent)
- Regardless of role, a user who owns a child record of an account(opportunity, case, contact) gains read acess on that account. can not overwrite this access
- sharing settings 'grant access using hierarchies' check mandatory
#### Sharing Rules
- grant additional record access to groups of users on an object-by-object basis
- Excepetions to OWD, Irrelevant for public data access models, **one direction giving**
- **Share which records** : Owned by certain users, Meeting certain criteria
- **From which users** : Public groups, Roles, Roles and subordinates, Queues (cases only)
- **To which users** : Public groups, Roles, Roles and subordinates
- **What lvl of access** : Read Only, Read / Write
- **Public Groups** : admin defined goruping of users (individual users, roles, roles and subordinates, other public groups) self one sharing rule -> one big public group
- **Manager Groups** : if enabled, allows users to share records with their managers and manager subordinates groups
- recalculate non working hours
#### Teams and Manual Sharing
- **Teams :** 
	- **Opportunity team**
		- define roles for team members and set record-lvl access
		- can be viewed in list views and on reports
		- only give access to the one object
	- **Account team**
		- Read or Read/Write access & related objects (contacts, opportunities, cases)
		- define an account role for each team member
		- view an account team on the account page related list
	- **Case team**
		- allow users to grant access to their cases and related records to users, contacts, or add predefined case teams
		- admins can define member roles, create **predefined case teams**, configure assignment rules to automatically add case teams to cases, use up to three different teams for a single case
		- ![610](Pasted%20image%2020260526174404.png)

- **Manual Sharing:** allow users to grant one-off access to their individual records for users, roles, roles and subordinates and public groups
	- record owners, their managers in the role hierarchy, and admins (sharing button)
	- permanantly deleted when the owner of the record is deactivated, or changed to anotehr owner
#### Restriction rules
- restict access for certain users to only specific records
- object manager
- **supported for the following objects :** custom objects, contracts, tasks, events
  +external objects, quotes, time sheets & entries
- ![](Pasted%20image%2020260526180513.png)
+ ![](Pasted%20image%2020260526180130.png)
- ![](Pasted%20image%2020260526180100.png)
#### Data(Information) privacy
- the proper handling of data including consent, notice, and regulatory obligations 
- GDPR, CCPA
## <font color="#00b0f0">Lesson 5</font> Customize Standard Functionality
#### <u>evaluating before constructing your org</u>
- standard functionality: use
- declarative: configure
- appexchange: buy / get
- programmatic: develop

#### Custom Objects
- CRRSS (configurable, Relational, Reportable, Searchable, Securable)

#### Standard fields
- All objects have a predefined set of fields
- can't delete them but can use FLS and page layout techniques
- **Customizable**: change the field label, add help text, add or edit values in picklists, add or edit lookup filters, set field history tracking, change the format of auto-number fields (classic only) rename tabs and labels (Label O / API Label X)
- data classification fields

#### Custom fields
- new fields created on any standard or custom object
- object customization, type changing, deleting
- data loss when editing and deleting custom fields
	- field's data will be lost, list views based on the field will be deleted, Assignment and escalation rules may be affected
	- should only modify fields with no data, or consider using new fields
	- max 15 days recovery chance : undelete or permanently erase them
- Creating a new custom field
	- **Select Data Type** (Schema builder)
	- ![](Pasted%20image%2020260527111046.png)
	  Picklist, Roll-up Summary (Account -> Opportunity)
	- Enter Details (Define field attributes)
		- Description
		- Help Text
		- Required
		- Unique
		- External ID
		- Default Value
	- Set FLS
	- Add to Page Layouts

![](Pasted%20image%2020260527181147.png)
#### Picklist fields
- regional: APAC, EMEA, LATAM, US, Canada
- single or multi-select - predefined list
- data entry speed up, data quality only allowing permissible values, facilitatie searching, reporing, filtering
- list of custom picklist fields with inactive values (picklist settings)
	- useful for bulk deletion
- **Global Picklists Value Sets** : across objects, restricted on the objects and can only be edited from the global setting (reuse) region / address Picklist Value Sets
- **Dependent Picklists** : Controlling / Dependent
	- select a value in a controlling picklist, which filters the values available in a dependent picklist (+validation rule, page layout dependent required)
	- multi-lvl dependencies
	- ![](Pasted%20image%2020260527113401.png)
#### **Object relationships**
- defined on the child object using a custom field
- types: 
	- **Lookup**
		- Lookups: fields that allow users to select a record from another object during data entry, A use B field values, parent(B)-child(A) relationship, A->B
		- independent sharing
		- lookup field on the child can be optional or required
		- **lookup filter**: limit the records available in the lookup
			- Source - Other fields on the same record
			- Target - Fields on the records of the lookup object
			- User - Fields on the user's record, profile, and role
			- Directly related to the Target - Fields on record
			- can be multiple layers deep
			- child can have up to 40 parents
			- lookup field on page layout depends on required / optional choice
			- Roll-up summary fields not allowed
	- **Master-Detail
		- Access to a detail record is inherited from the master record
		  (Master visible - Detail visible) unable to manually share detail records
		- the detail record is automatically deleted when the parent is deleted
		- the parent reference is always required on the child record
		- lookup filter, allow reparenting
		- **Junction Object**: a custom object with two Master-Detail relationships allows to model a many-to-many relationship (visible visible visible)
		- up to 3 layers deep, standard object cannot be a child
		- Relationship field on page layout is required
		- Roll-up summary fields allowed
		- account - opportunity, contact
	- **Hierarchy (User object only)**
	- **Self Relationship (Lookup) (For Hierarchy-user, company, campaign)** Objects
#### Custom formula fields (mirror)
- define calculations that reference other fields to display new numeric, text, date, or checkbox values specific to your business requirements
- **Formula Fields**
	- Read-Only
	- can reference fields on the same object, or a parent or lookup object
	- can't reference encrypted, description, or custom long text area fields
	- are not searchable, or available for lead conversion or the weekly export service
- custom field wizard
	- simple formula : numerical fields from the same object
	- advanced formula : funtions, non-numberical fields, fields from parent objects
- **Cross-object formulas**
	- reference fields only from parent objects
	- access fields from upto 10 parent levels
## <font color="#00b0f0">Lesson 6</font> Customize the UI
#### App Manager
- ![](Pasted%20image%2020260528172626.png)
- Lightning Experience App Manager
- view, create, visible, manage
#### Home page
- standard or custom lightning components
- update component properties
- assignable to user profiles
- Setup Home Page < special
#### List views
- save list views for future use
- filter on a specific fields
- search the field data in list views
- sharing settings
- **grid, kanban, split**
- edit records
- appropriate name, visibility, up to 15 cols, up to 10 filters
#### Page layout
- controls fields, sections, related lists, buttons
- sections - field container wrapper (Dynamic forms visibility)
	- layout control, tab order control
- Lightning App Builder(Edit Page)
- Page Layout Editor(Object Manager) - fields, related lists, quick actions, buttons
	- sstandard / custom button, quick action for list view
- Can be assigned to a profile
#### Enhanced related lists
- can show up to 10 cols, resize and sort cols, perform mass actions, wrap text
#### Buttons, Links, Actions
- Buttons, Links
	- serve the same function - send a user to an external place or to launch OnClickJavaScript or Visualforce
- Actions
	- Add functionality to Salesforce data
	- create records, update records, log calls (global)
	- object-spcific actions
#### Record types
- Nowadays, the trend is to minimize to a single page layout per profile, utilize record types strictly for picklist and process control, and dynamically drive fields and layouts using Dynamic Forms and Permission Sets.
- allow admins to offer users different page layouts and picklist values for different business scenarios, based on their profiles
- each object has a default master record type, but you can create new ones
- ![](Pasted%20image%2020260528180008.png)
- ![](Pasted%20image%2020260528180408.png)
- Opportunities, cases, solutions, leads - record type
- ![](Pasted%20image%2020260528180905.png) states exist (account doesnt require a business process to be created)
- allow users to access multiple page layouts per object
- allow unique data to be gathered for different business scenarios
- can be assigned to users via their profiles or permission sets(dynamic forms)
#### Path
- guides users along the steps in a process
- helps users succeed with step-specific guidance (tips, links, company policy info)
- can be customized
## <font color="#00b0f0">Lesson 7</font> Data Management
#### Data backup options
- **Reports**
	- csv, excel, db
	- manual, automated
- **Data Loader (io)**
	- export specific data to csv, xls, xlsx
	- manual
- **Data Export**
	- obtain a complete set of Salesforce data for archiving
	- export to csv
	- include images, documents, attachments
	- Salesforce Files, Salesforce CRM Content document versions
	- can be automated, scheduled, emails you when the zip files are ready
#### **Managing Metadata**
- Change Sets
	- Copy meta data from production to a sandbox or from one sandbox to another
- Sandbox Refresh
	- By refreshing a related sandbox, configuration metadata is copied over automatically
- Force.com Migration Tool
	- Java/Ant-based command-line utility for moving metadata between a local directory and a Salesforce org
#### Data Import wizard
- import new records, update existing records
- accounts, contacts, leads, solutions, campaign members and custom objects
- solution: a standard object which records solutions for customer complaints or frequently common issues (linked to Cases)
- matching types
	- duplicates identification when you add new records
	- matches records when you update existing ones
	- ![362](Pasted%20image%2020260601174247.png)
- import fewer than 50,000 records
- prevent duplicates when importing new records
- choose whether or not to trigger workflow rules and processes
#### Data Loader
- bulk import or expor of data, client based requried installation and authentication
- insert, update, delete, export, upsert for both standard and custom objects for up to 5,000,000 records
- obtain salesforce record IDs
- load objects such as products or opportunities
- save mappings for later use
- scheduling not supported
- to individual csv? unable to restore relationship
- metadata extraction not supported
#### Dataloader.io
- 100% cloud solution, manage bulk data updates
- import, export, delete
- Salesforce login using oAuth, no signups or security tokens required
- create reusable tasks and schedule them periodically
- find related IDs while mapping
- ![](Pasted%20image%2020260601174939.png)
- just csv peridoic export, not a lot data
#### Data import best practices
1. Create any necessary fields prior to the import
2. Clean up data prior to import
3. export any necessary record ID fields
4. Prepare and upload a test batch
- Don't perform updates to existing records duing normal business hours
- Check if there is any automation set up (flow)
- if (owner.field.equals("")) { default_owner = importing_user};
- why fail
	- Universally required fields
	- Unique fields
	- Data validation rules
	- Picklist value not allowed
#### Mass delete records
- delete <u>standard object</u> records meeting specific criteria
- to be deleted records will be displated
- will alert you of any child records that would also be deleted
- Best practice
	- requrest or perform a backup before using it
- Deleted records are stored in the recycle bin for another 15days, unless you choose permanently delete
- recycle bin
	- max 15 days
	- my recycle bin is available to all users
	- records can be restored by clicking Restore
	- permanently delete records by selecting them and clicking Delete
#### Mass transfer tool
- transfer multiple accounts, leads, service contracts, and custom objects from one user to another
- depending on the object, options to transfer related records might exist
- deactuvate, freeze
#### Field history tracking
- enables it on an object to track changes on up to 20 standard or custom fields on each object
- changes can be viewed on a record's history related list or through history reports
	- Date and time, user, old and new values (not on multi-select picklists and large text fields)
#### Data validation
- Ensure the integrity of data **before** it is saved
	- System Data Validation (runs first)
		- Out-of-the-box validation
		- setting simple field properties to ensure valid data entry
			- field data type
			- required field
			- unique field
	- custom validation rules (runs second)
		- enforce more complex conditions (one or more fields, specific to your biz processes)
- mandatory
#### Duplicate leads
- Web-to-lead : Forgetting to search for a lead (already existing leads)
- Importing from lists : Private sharing model
- **Merge** : lead record - duplicates - master - field values to keep - confirm
	- can merge 2 or 3 leads at a time
- **Duplicate Management** : helps to manage duplicates for Biz accounts(B2B), contacts leads, person accounts(B2C), records created from custom objects
	- ![](Pasted%20image%2020260601181037.png)
	- ![](Pasted%20image%2020260601182917.png)
## <font color="#00b0f0">Lesson 8</font> Declarative Automation
#### Overview
- Lead
	- Web-to-Lead
		- custom fields
			- ensure fields capture the information you need from the website and specify how they map when the lead is converted
			- check default status, record types and lead settings
		- queues
			- create any needed queues
			- records await processing by assigned members
			- queue members can contain any combination of public groups, roles, roles + subordinates, and users
			- when you create a queue, a view is automatically added to the object's(such as lead, case, or custom object) list views
			- members of the queue are free to accept records (lead, case, or custom object) from the queue
			- assisgn tasks to a queue to share work efficiently. when a task is assigned to a queue, any of the members form that particular queue can pick the task, which gives all members of a queue full access to the record
		- assignment rules
			- create or activate a rule that determines HOW leads are assigned
		- email templates
		- org-wide email addresses for auto-responses
		- auto-response rules to send targeted email responses
		- when you enable it, you specify a default lead creator, and the email response template used when no auto-response rules apply
		- once you have enabled the feature, you can select any field on the lead or case object to be generated in html(web form)
	- Assignment Rules : automate lead routing
		- assign leads or cases to individaul users or queues vased on the criteria
		- only one rule can be active at any time
		- each rule can contain multiple entries, routing records according to several criteria
	- Auto-Response Rules : automate responses to the new lead
		- lead/case  
		- respond to the web submission of leads or cases with a specific email, bssed on the criteria
		- only one rule can be active at any time
		- each rule can contain multiple entries, sneding a different email template based on the criteria you set
		- users do not get auto-responses
	- Limit - 500 per 24 hour period
- Case
	- Web-to-Case
	- Email-to-Case
		- custom fields
			- ensure your fields capture the information you need from the website
			- set the default case status
		- queues
			- create any needed queues
		- assignment rules
			- create or activate a rule that determines how cases are assigned
		- email templates
			- create any necessary email templates
		- org-wide email addresses
			- create any necessary org-wide email addresses from which to send auto-responses
		- auto-response rules
			- create or activate a rule to send targeted email responses
		- automatically creates a case from an inbound email
		- uses the sender's email address to associate a contact to the case
		- uses email content to auto-populate case fields
		- automatically associates customer email replies, including attachments, with the case
		- triggers assignment, auto-response, escalation, workflow rules, and processes
	- Escalation Rules (Cases only)
		- automatically re-assign a case and/or notify a user if the case is not dealt with within a certain period of time
		- choose to change owner to a queue or to another user
		- configure rule entries to define the order, criteria, and escalaation actions
		- specify time frame (mins or hours) for escalation if case has not been closed
		- consider enabling early triggers in support settings
	- Limit - 5000 per 24-hour period
- Opportunities
	- Big Deal Alerts
	- Update Reminders
- All Objects
	- Workflow
	- Process Builder
	- Approval Processes
	- Validaiton Rules
	- Flow
#### Email templates (lightning and classic)
- should be created before using in automations
- communication templates are accessed by the folder they are saved in
	- access levels include Read & Read/Write
	- Accesible by all users, hidden by all users, or by certain groups (roles, roles and subordinates and public gorups)
- lightning email templates
	- increase productivity and ensure consistent messaging
	- merge fiels, field data from Salesforce records
	- Email action on a record page / Email Templates tab
- Enhanced letterheads
	- header footer standardization (company's logo and contact info, legal disclaimers and subscription links)
	- rich text editor or custom HTML
	- merge fields, images, and links
#### Data Validation
- ensure the integrity of data before it is saved
- **System Data Validation (runs first)**
	- Out-of-the-box validation
	- setting simple field properties to ensure valid data entry
		- Field data type
		- Required field
		- Unique field
- **Custom Validation Rules (runs second)**
	- Validation you build
	- enforce more complex conditions, involving one or more fields, specific to your business processes
	- can contain a formula or expression that evaluates the data in one or more fields and returns a value of "True" or "False"
	- ![](Pasted%20image%2020260609174223.png)
#### Required and Unique fields
- system lvl, force users to always enter a value, or to prevent records with duplicate values
- hard requirements applying to UI and API
- ![433](Pasted%20image%2020260609173916.png)
- making a field required on a page layout (UI only) is considered a "soft" requirement
#### Lead Conversion
- when a lead is converted by a user
	- the info from the standard lead fields is inserted into standard account and contact fields (mapping fields to an opportunity object record is optional)
	- custom lead fields must be mapped manually (to custom Account, Contact, and Opportunity fields)
		- same data type required
		- ![](Pasted%20image%2020260609181220.png)
#### Other ways to provide support
![](Pasted%20image%2020260611175718.png)
![](Pasted%20image%2020260611175737.png)
#### Workflow rules (deprecated)
- sets workflow actions into motion when certain conditions are met
- actions can take place immediatelyl, or on a specific date, according to a trigger
- ![](Pasted%20image%2020260611180311.png)
- considerations
	- tasks
		- the only type of record Workflow can create
		- can be assigned to user, role, record owner, record creator, or account team
		- a single task can only be assigned to one user (auto assigning to the owner of the record)
	- field updates
		- target or parent object updates only
		- field updates occur before email alerts, tasks, and outbound messages
	- outbound messages
		- sends info out of salesforce to a designated endpoint (external service,,)
#### Process builder (deprecated)
- business processes automation with multiple criteria nodes
	- create a record, update records, send email post to chatter, send custom notifications, use an action, submit for approval, launch a flow, launch a process, call apex, manage quip documents
	- ![222](Pasted%20image%2020260611181019.png)
#### Approval processes
- ![](Pasted%20image%2020260611181126.png)
- ![](Pasted%20image%2020260611181315.png)
- ![673](Pasted%20image%2020260611181329.png)
![](Pasted%20image%2020260624105814.png)
## <font color="#00b0f0">Lesson 9</font> The Future of Automation: Flow
## <font color="#00b0f0">Lesson 10</font> Create New with Clicks
## <font color="#00b0f0">Lesson 11</font> Analytics
#### Reports
- lists or summaries, enable to aggregate and analyze data in different ways
- **Custom reports**
	- created from existing reports
	- built from scratch using available report types
	- must be saved in a custom, private, or public folder
	- can be overwritten or deleted
- **Dashboard folders**
	- access to reports and dashboards is controlled
	- building subfolders to add more categories while access is still granted at the parent folder lvl
	- different groups of users different access to the same folder 
	- share with users, roles, roles & subordinates, public groups
	- view, edit, manage permission
- Overview
	- ![](Pasted%20image%2020260527115726.png)
- #### **Report types** : Predetermined combinations of related objects and fields used as starting points for new custom reports
	- the objects and fields available
	- the filters available (based on primary object)
	- the default cols
	- **Standard** : available by default for building reports on standard and custom objects and their related objects
		- new custom fields are automatically added to standard report types
		- standard report types show 'with'(**inner join**) relationships
			- Account with Account Teams : only accounts that have related account teams
	- **Custom** : With or Without (outer join)
- #### **Report formats**
	- **Tabular**
		- Simplest and fasterst way to look at data
		- best for creating lists of records or a list with a single grand total
	- **Summary**
		- Similar to tabular reports, but allow goruping rows of data, view subtotals, and create charts.
		- can be used as the source report for dashboard components
		- can group up to 3 x-axis(horizontal) rows maximum on a Summary report
	- **Matrix**
		- Similar to summary reports, but allow you to group and summarize data by both rows and columns
		- Good for comparing related totals or comparing values in several fields
		- can be used as the source report for dashboard components
		- Must have minimally 1 x-axis field group before adding 1 vertical filed to make a Matrix report
		- can group up to a max of 2 x-axis grouping fileds and 2 y-axis (vertical) grouping fields max
	- **Joined**
		- Combine multiple views (blocks) of related info in a single report (up to 5 blocks)
		- each block 'sub-report' can display data from the same report or from a different report type
		- can be used as the source report for dashboard components but must have a chart
	- ![](Pasted%20image%2020260527161756.png)
- #### **Report groupings and summaries**
	- have implications for subtotals and grand totals in reports
	- ![585](Pasted%20image%2020260527135725.png)
- #### **Report filters and filter logic**
	- Add up to 20 additional filters to a report
	- and, or, not logic
	- () parentheses (()) nested parentheses offset priority conditions
- #### Summary formulas
	- create calculated summaries of your numerical fields
	- add up to 5 custom summary formulas to summary and matrix reports
	- reference formula fields, but not other summary formulas
	- only display on summary rows, not detail (record) rows
- #### Row level formulas
	- adds a row-level formula column to the report that makes calculations on every report row
	- text concatnation, data comparision, simple conditional statements
- #### Conditional formatting
	- Conditional Formatting Rules (custom ranges and colors)
	- summary or matrix reports
	- mus contain at least 1 summary field or custom summary formula
	- Lightning Experience, up to 5 rules & define custom colors for each range
	- breakpoint values & bin range colors
- #### Report Chart
	- **Chart:** graphical representations of the data in the summary rows or columns of a report
	- no impact on the report
	- Types
		- **Horizontal Bar** : Compare many items
		- **Vertical Bar (Column)** : Fewer items or over time
		- **Stacked Bar Chart** : Compare absolute values side by side
		- **Donut** : Compare share of total
		- **Funnel** : Sales process
- #### Export
	- csv xlsx xls
	- report charts will not export
- #### Subscribe, Schedule, and Send
	- email, the folder should be shared
	- add conditions based on sum of the amount or record count in report to be notified (conditional notification)
	- run report as me -> data under my permission
	- run report as 'someone' (standard) -> data under their permissions
- **Running User**
	- you run the report, and recipients see report data in the emailed report as you
	- they may see more or less data than they normally see
	- data under their permissions
#### Dashboards
- visual representation using multiple custom reports data
- use a running user to determine what data is visible
- can have up to 20 components per dashboard
- display data as of the last time the dashboard was refreshed
- from source report to dashboard component
	- **Component** : use the first summarized field in the source report
		- Table, Charts, Gauge, Metric
		- Horizontal Bar: Compare many items
		- Vertical Bar (Column): Fewer items or over time
		- Line: Over time
		- Stacked Bar Chart: Compare absolute values side by side
		- Gauge: Show a single value in a range of custom vaues
		- Donut: Compare share of total
		- Tables: Show conditional highlighting and chatter photos
		- funnel: sales process
		- metric: display one key value
		- scatter chart: show correlation between two measures
	- **Properties**
		- must have the access to the folder in which the dashboard is saved
		- Me
		- Another Person (Fixed)
		- The Dashboard Viewer (Dynamic)
			- can't schedule refreshes for dynamic dashboards and must be refreshed manually
		- Optionally, let viewers choose whom they view the dashboard as
	- #### Subscribe, Schedule, and Send dashboards
		- subscrive yourself and other users, gorups, or roles to receive refreshed dashboards results by email on a schedule that you set
		- All email recipients must have access to the folder the dashboard is saved in
		- Optionally, subscribe to a dashboard to be refreshed without receiving refreshed results by email
- #### Analytics Home
	- search for, access, and create both reports and dashboard from a single tab
	- view recently updated, recently viewed, and favorite analytics
	- Create Collections to organize analytics content
## <font color="#00b0f0">Lesson 12</font> The Agentic Enterprise
#### AI agents
- handle routine tasks so humans can focus on creativity, relationships & impact
#### Salesforce
- agentic enterprise
	- 
- **Agentforce 360** : humans, agents, apps & data
	- no code & vibe code
	- a set of tools
		- Agentforce Builder : create and customize agents
			- Topics, Actions (flows, Apex, prompts, APIs)
		- Agentforce Atlas Reasoning Engine : takes action
			- RAG, Advanced Planner
	- a suite of agents
		- autonomous
			- Agentforce Service Agent, Agentforce Lead Nurturing, Agentforce Personal Shopper
		- assistive
			- Agentforce Employee Agent, Agentforce Sales Coach, Agentforce Campaign Optimizer
- ![](Pasted%20image%2020260527160337.png)
- Siloed systems & data, Manual workflows, Reactive support, Burnout staff
	- Fully unified data, Conversation, AI-first, Always-on experiences, Ability to focus on mission
- Einstein Trust Layer: Role, Data, Actions, Guardrails, Channel
	- secures all operations through data masking and toxicity detection
- plan, evaluate, refine cycle
- Human-in-the-loop
- ![](Pasted%20image%2020260527161326.png)
#### Prompt
- question, instruction, context
- UI, AI Model, Data
- Prompt Template
	- Sales Email, Field Generation, Flex(ible)-invocable, Record Summary
![](Pasted%20image%2020260527161439.png)
#### Troubleshooting Agents
공유해주신 링크(`ai.copilot_troubleshoot.htm`)는 세일즈포스의 GenAI 기능인 **Einstein Copilot(현재의 Agentforce Agent)의 작동 오류 및 성능 문제를 진단하고 해결(Troubleshooting)하는 공식 가이드** 페이지입니다.

해당 문서의 핵심 내용을 핵심 진단 도구와 문제 유형별 해결 방법으로 분류하여 정리해 드립니다.

### 1. 핵심 문제 해결 프로세스 & 도구

문서에서 가장 중요하게 강조하는 진단 도구는 '향상된 이벤트 로그(Enhanced Event Logs)'입니다. 에이전트가 왜 엉뚱한 대답을 하거나 작동하지 않는지 추적할 수 있는 블랙박스 역할을 합니다.

- **향상된 이벤트 로그(Enhanced Event Logs) 활성화:** * **기능:** 에이전트 세션 내에서 발생한 이벤트뿐만 아니라 사용자가 보낸 실제 메시지, 에이전트의 내부 판단 과정, 발생한 에러 코드 등을 한곳에서 실시간으로 확인할 수 있습니다. (7일간 저장)
    
    - **설정 경로:** `Setup -> Agentforce Agents -> 해당 에이전트 선택 -> 'Keep a record of conversations with enhanced event logs...' 체크 후 저장`
        

### 2. 주요 문제 유형 및 트러블슈팅 방법

#### ① 에이전트(코파일럿)가 사용자의 요청을 이해하지 못하거나 엉뚱한 행동을 할 때 (Intent Recognition Error)

- **원인:** 에이전트에 할당된 액션(Actions)의 지시사항(Instructions)이 모호하거나 부족하기 때문입니다.
    
- **해결책:** * 이벤트 로그를 확인하여 시스템이 유저의 입력을 어떤 액션으로 매핑하려 했는지 확인합니다.
    
    - Agentforce Builder(에이전트 빌더)에서 액션의 Description(설명)과 Instructions(지시사항)을 자연어로 더 구체적이고 명확하게 수정합니다. (예: "언제 이 액션을 실행해야 하는지" 명시)
        

#### ② 데이터를 제대로 찾아오지 못할 때 (Knowledge / Data Retrieval Issue)

- **원인:** 지식 소스(Knowledge Source)나 레코드 검색 필터 셋팅이 잘못되었거나, Data Cloud 연결에 문제가 있는 경우입니다.
    
- **해결책:** * 에이전트가 참조하는 **Knowledge Base(지식창고)의 싱크 상태와 권한을 확인**합니다.
    
    - 유저의 프로필/권한 세트(Permission Set)가 해당 데이터 오브젝트나 필드를 읽을 수 있는 권한(`Read` 권한)을 가지고 있는지 체크합니다.
        

#### ③ 시스템 에러 및 예외 발생 시 (System Error / Drop)

- **원인:** 세션 타임아웃, LLM(거대언어모델) 게이트웨이 오류, 혹은 Apex 클래스/Flow 오류가 얽힌 경우입니다.
    
- **해결책:** * **Event Log의 Session ID**를 클릭하여 구체적인 에러 메시지를 확인합니다.
    
    - 에이전트가 호출하는 내부 **Flow(플로우)나 Apex Action**에 버그가 없는지 디버깅 툴로 확인합니다.
        

### 💡 관리자를 위한 권장 테스트 전략

가이드에서는 에이전트를 운영 환경(Production)에 배포하기 전, **Agentforce Testing Center** 및 Builder 내부의 시뮬레이터(Simulate/Live Test Modes)를 활용하여 시나리오 테스트를 반복할 것을 권장하고 있습니다.

문제가 생겼을 때는 [Setup -> Event Logs]에서 사용자의 실제 발화와 시스템 반응 속성(Dropped 이유 등)을 교차 검증하는 것이 문제 해결의 첫걸음입니다.

공유해주신 링크(`ai.agent_setup_explore_types.htm`)는 세일즈포스의 자율형 AI 에이전트 서비스인 **Agentforce가 제공하는 에이전트의 종류(Types)와 비즈니스 목적별 아키텍처**를 설명하는 공식 가이드 페이지입니다.

세일즈포스 에이전트 유형을 한눈에 파악하실 수 있도록 핵심 내용을 명확하게 정리해 드립니다.

### 1. Agentforce 에이전트의 3가지 핵심 유형

세일즈포스는 비즈니스 요구사항과 대상(Target)에 따라 크게 3가지 형태의 에이전트를 제공합니다.

#### ① 서비스 에이전트 (Service Agent)

- **목적:** 고객(End-User)을 직접 응대하는 자율형 고객 서비스 에이전트입니다.
    
- **특징:** 과거의 시나리오 기반 챗봇과 달리, 대화의 문맥을 이해하고 세일즈포스 데이터 및 지식창고(Knowledge)를 기반으로 직접 문제를 해결합니다. (예: 반품 처리, 예약 변경, 주문 추적 등)
    
- **연결 채널:** 웹챗(Messaging for In-App and Web), 왓츠앱, SMS 등 다양한 고객 접점 채널에 연동할 수 있습니다.
    

#### ② 직원 에이전트 (Employee Agent / 기존 Copilot)

- **목적:** 내부 직원(사내 사용자)의 업무 생산성을 높여주는 AI 비서입니다.
    
- **특징:** 세일즈포스 화면 내부나 슬랙(Slack) 등에서 작동하며, 직원의 지시에 따라 복잡한 작업을 대신 수행합니다. (예: "오늘 마감인 영업 기회 요약해 줘", "특정 고객사 미팅 준비용 브리핑 문서 작성해 줘" 등)
    

#### ③ 파트너 에이전트 (Partner Agent)

- **목적:** 기업의 외부 비즈니스 파트너나 유통업체(Distributor)를 지원하는 에이전트입니다.
    
- **특징:** Experience Cloud(익스피리언스 클라우드) 포털 등에 배치되어, 파트너사가 제품 정보를 조회하거나 리드(Lead)를 등록하고 등록된 계약을 갱신하는 등의 복잡한 B2B 프로세스를 자율적으로 도와줍니다.
    

### 2. 에이전트 유형을 선택하고 빌드할 때의 기준

문서에서는 에이전트를 구축하기 전에 다음 요소들을 고려하여 적절한 유형을 탐색하고 설정하라고 안내합니다.

- **사용자 경험(User Experience):** 이 에이전트와 대화할 대상이 '익명의 웹사이트 방문자'인지, '로그인한 내부 직원'인지에 따라 보안 및 대화 톤앤매너를 다르게 설계해야 합니다.
    
- **액션 및 권한 범위(Actions & Permissions):** 에이전트 유형에 따라 접근할 수 있는 세일즈포스 오브젝트 권한과 실행할 수 있는 플로우(Flow) 및 API 범위가 달라집니다. 내부 직원용 에이전트는 상대적으로 더 넓은 데이터 접근 권한을 가집니다.
    
- **데이터 소스(Data Sources):** 에이전트가 신뢰할 수 있는 답변을 하도록 Data Cloud, Salesforce Knowledge, 내부 레코드 필드 등을 어떤 방식으로 에이전트 유형에 결합할지 정의해야 합니다.

## CRM Basic
#### Certifications
- Foundation
	- Admin
- Developer
	- Platform Developer I
- Architect
- Marketing
	- MC Email Specialist
	- MCE Adminstrator
	- MCAE Specialist
- Salesforce Consultant
	- Data, Sales, Service Cloud Consultant
- Agentforce Specialist

#### Questions
- 라이선스
	- Company setting
- Business Hours
	- 영업시간
	- login hours랑 다름(이때만 로그인 가능해요~)
- Fiscal Year, Multi-Currency
	- 한번 활성화하면 비활성화 불가
- Data Protection and Privacy - Individual Obj

#### User
- Username - 이메일 형식, 중복x, 체크방식 추가 기능
- 비밀번호 까먹으면 - reset
- 유저 여러명 넣어볼 수 있음, 필드가 적음, data loader
- User360 - 어디에 할당되어 있는지
- 퇴사자 - active 지우기, 유저 할당 license 반환된
- 잠시 떠나있으면 Freeze
- Login as
- internal 내부 직원, external 외부 사용자 조회 필요할 때

영업, 프리세일즈 (demo 엔지니어), 서비스 엔지니어

- app builder field location dynamic form field filter (set field visibility) 
	- Save - Activate
- page layouts - mobile ui, button 
- Company Layouts - Kanban, highlights panel

#### Einstein Scoring
- Opportunity, Lead
- Einstein Lead Scoring
- Forecasting
- Sales Forecasting (quantity)

#### Campaign
- Member : target
- Hierarchy : Group based management
- Influence : contribution to opportunities
- Budgeted Cost / Expected Revenue : for Reporting

#### escalation rules

#### service
- knowledge

#### Omni Channel
- Case, Lead handling issues allocation
- Assignment Rule 대비 better
#### Entitlement & Milestone
- SLA(Service Level Agreement)
	- 고객 제공 서비스 수준 명시 계약
- Entitlement
	- 개별 Account 지원받을 수 있는 서비스 지원 레벨 정의
	- Account와 Look-up 관계
- Entitlement Process & Milestone
	- 최초 응답 시간, 해결 기한 SLA 포함 시, 각 단계별 완료 시한 관리 기능

#### Task & Event
- activity timeline

crm jpkt

#### Chatter
- group - private, public, unlisted, broadcasting

#### App Exchange
- agentexchange
- component based
- consultant

#### Data Management Tool
- Import Wizard - 소량, 중복 방지, workflow triggering yes or no
- Data Loader - import, export, delete&bulk
- 현업:chrome extension

#### Audit Trail
- Meta data tracking

#### Data validation
- Field Data Type, Required field, Unique field

#### Merge dulicate leads
- business accounts, contacts, leads, person accounts(b2c), custom objects' records

#### Report and Dashboard folders
- Report filters and filter logic
- Bucket Column (Salutation to Gender)

#### Running User
- Report vs Dashboard

#### Automation
- Flow - 50 versions, only one is allowed at a time
- review, decision making - approval process(re)
	- examples

Dev free trial

## Agentforce
#### Prompt builder
- Grounding - adding context
- Trust Layer
- 추론 - Agentic AI loop, 액션 - flow, apex
- Agent Builder - Topics(겹침ㄴㄴ), Instructions(명확한 지시, 긍정>부정), Actions

#### Agentforce inside sales
- performed by agents
- Service, Sales, Mktg & SDR

salesforcego
einstein setup

agentforce studio

Dev edition