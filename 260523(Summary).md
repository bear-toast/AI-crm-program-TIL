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
- Row = Record
- Column = Field
- **Standard objects**
	- Account, Contact, Opportunity, Lead, Campaign, Case, User
	- ![151](Pasted%20image%2020260522173259.png)![223](Pasted%20image%2020260522173334.png)
	- **Object Manager** : fields, page layouts, compact layouts customizations (in Setup : Salesforce backend)
		- handles standard, custom objects
	- **Schema Builder** : objects relationships

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
- Login hours, Login IP ranges, Record Type & App (defaults), Page Layout Assignment

#### Permission set
- grants additional permissions to specific users that layer on top of their existing profile
- assign to users from the permission set / user record
- **user's total access = profile + permission sets**
- User Permissions (system / App), Object Permissions (CRED), Field Permissions, Tabs, Record Types & Apps (not defaults), Connected App Access, Apex Classes, Visualforce Pages, Gustom Permissions

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
  PRIVATE -> PUBLIC READ-ONLY -> PUBLIC READ/WRITE
- **Sharing settings** : Public, Hybrid, Private
- ![](Pasted%20image%2020260526170941.png)
- Default Internal open, Default External Access closed
#### Role Hierarchy
- Users in **higher roles** inherit the special ownership privileges (full access) on all records owned by users in roles below them
- Role hierarchies =/=  org charts
- custom object records do not have to be inherited
- when creating a new role, define the lvl of access an account owner will have to the related records owned by users who are not their subordinates (Contact, Opportunity, Case - OWD set for each object: No Access, View, or Edit dependent)
- Regardless of role, a user who owns a child record of an account(opportunity, case, contact) gains read acess on that account. can not overwrite this access
#### Sharing Rules
- grant additional record access to groups of users on an object-by-object basis
- Excepetions to OWD, Irrelevant for public data access models, **one direction giving**
- **Share which records** : Owned by certain users, Meeting certain criteria
- **From which users** : Public groups, Roles, Roles and subordinates, Queues (cases only)
- **To which users** : Public groups, Roles, Roles and subordinates
- **What lvl of access** : Read Only, Read / Write
- **Public Groups** : admin defined goruping of users (individual users, roles, roles and subordinates, other public groups) self one sharing rule -> one big public group
- **Manager Groups** : if enabled, allows users to share records with their managers and manager subordinates groups
#### Teams and Manual Sharing
- **Teams :** 
  **Opportunity team**
  define roles for team members and set record-lvl access
  can be viewed in list views and on reports
  only give access to the one object
  **Account team**
  Read or Read/Write access & related objects (contacts, opportunities, cases)
  define an account role for each team member
  view an account team on the account page related list
  **Case team**
  allow users to grant access to their cases and related records to users, contacts, or add predefined case teams
  admins can define member roles, create **predefined case teams**, configure assignment rules to automatically add case teams to cases, use up to three different teams for a single case
  ![610](Pasted%20image%2020260526174404.png)

- **Manual Sharing:** allow users to grant one-off access to their individual records for users, roles, roles and subordinates and public groups
	- record owners, their managers in the role hierarchy, and admins (sharing button)
	- permanantly deleted when the owner of the record is deactivated, or changed to anotehr owner
#### Restriction rules
- restict access for certain users to only specific records
- object manager
- **supported for the following objects :** custom objects, contracts, tasks, events
  +external objects, quotes, time sheets & entries
- 
- ![](Pasted%20image%2020260526180513.png)
+ ![](Pasted%20image%2020260526180130.png)
- ![](Pasted%20image%2020260526180100.png)
#### Data(Information) privacy
- the proper handling of data including consent, notice, and regulatory obligations 
- GDPR, CCPA
## <font color="#00b0f0">Lesson 5</font> Customize Standard Functionality
## <font color="#00b0f0">Lesson 6</font> Customize the UI
## <font color="#00b0f0">Lesson 7</font> Data Management
## <font color="#00b0f0">Lesson 8</font> Declarative Automation
## <font color="#00b0f0">Lesson 9</font> The Future of Automation: Flow
## <font color="#00b0f0">Lesson 10</font> Create New with Clicks
## <font color="#00b0f0">Lesson 11</font> Analytics
## <font color="#00b0f0">Lesson 12</font> The Agentic Enterprise
