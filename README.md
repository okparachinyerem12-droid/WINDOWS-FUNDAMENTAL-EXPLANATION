# WINDOWS-FUNDAMENTAL-EXPLANATION
# WINDOWS FUNDAMENTALS: OPERATING SYSTEMS, ADMINISTRATION, ACTIVE DIRECTORY, GROUP POLICY AND EVENT LOGS

## Introduction

Windows administration is more than knowing how to operate a computer. It involves understanding how the operating system organizes information, manages users, controls access, enforces security settings, and records system activity. These functions are particularly important in information technology (IT) support, system administration, and cybersecurity.

This assignment examines the fundamental components of Windows administration, including its file system, command-line tools, local user management, Active Directory, Group Policy, and Windows Event Logs. It also explains how these components work together in practical IT environments.

# 1. WINDOWS FUNDAMENTALS

## 1.1 What is Microsoft Windows?

Microsoft Windows is an operating system developed by Microsoft that manages a computer's hardware and software resources and provides an environment in which users and applications can operate.

An operating system acts as an intermediary between the computer's physical components, applications, and users. It manages resources such as memory, storage, running processes, input devices, and network connections.

For example, when a user opens a web browser, Windows helps allocate the resources required to run it. When the user saves a document, Windows manages the operation of writing the data to storage.

Windows also provides security features, user account management, file permissions, and administrative tools. These features make it suitable for both personal computers and business environments.

From a cybersecurity perspective, understanding Windows is essential because many organizations use it to run business applications, store confidential information, and manage employee access. A security professional must understand how Windows operates before effectively investigating suspicious processes, unauthorized access, or system misconfigurations.

## 1.2 How does Windows organize storage using drive letters?

Windows commonly identifies storage volumes using drive letters followed by a colon. Examples include `C:`, `D:`, and `E:`.

A drive letter provides a convenient way to identify a storage volume or device. The letter `C:` is commonly assigned to the volume containing the Windows installation, although the exact arrangement depends on the computer's configuration.

A drive letter can represent a partition on a physical disk, a separate disk, a removable storage device, or another supported volume.

Windows uses paths to identify the locations of files and folders. For example:

`C:\Users\Student\Documents\assignment.docx`

This path indicates that the file named `assignment.docx` is located inside the Documents folder, within the Student user profile, on the C drive.

Drive letters help users and administrators distinguish storage locations, navigate directories, and identify where files are stored. However, two different drive letters do not necessarily represent two different physical disks.

In practical IT support, understanding drive letters helps technicians identify the Windows installation, locate user data, investigate storage problems, and determine whether a removable drive is accessible.

## 1.3 What is the purpose of the C:\Windows directory?

The `C:\Windows` directory contains many of the files and components required for the Windows operating system to function. These include system libraries, utilities, fonts, servicing components, and other operating system resources.

One important subdirectory is `C:\Windows\System32`, which contains many Windows utilities and essential system components. Despite the name, System32 is also used by 64-bit versions of Windows for important 64-bit system components.

Windows relies on these files to perform tasks such as managing hardware, supporting applications, and providing operating system services.

The directory is also involved in Windows maintenance and updates. Some of its contents are protected because unauthorized changes could affect system stability or security.

For example, deleting an essential system component may cause a Windows feature or application to stop functioning correctly.

In cybersecurity, system directories are relevant when investigating suspicious file activity. However, the presence of a file in a Windows directory does not automatically make that file legitimate. Its location, digital signature, behavior, and other evidence may need to be examined.

## 1.4 What is stored in the C:\Users directory?

The `C:\Users` directory normally contains the user profiles for accounts that have profiles on the computer.

A user profile stores user-specific files, preferences, and application data. Each user generally has a separate profile, allowing Windows to maintain individual settings and personal files.

Common profile directories include:

- `Desktop` — files and shortcuts associated with the user's desktop.
- `Documents` — documents and other personal files.
- `Downloads` — downloaded files.
- `Pictures` — image files.
- `Music` — audio files.
- `Videos` — video files.
- `AppData` — application-specific settings and data, including information that may be hidden by default.

For example, a document downloaded by a user named Student may be stored at `C:\Users\Student\Downloads`.

Separating profiles helps prevent users from unintentionally mixing their personal settings and files. Nevertheless, actual access depends on file permissions, account privileges, and the system configuration.

From a cybersecurity perspective, user profiles can provide useful evidence during an investigation. Downloaded files, application settings, and other artifacts may help an investigator understand activity on a computer. Some profile data may also contain sensitive information and must be handled appropriately.

## 1.5 What is the difference between Program Files and Program Files (x86)?

These directories are commonly used to store installed applications. On 64-bit Windows, they generally separate applications according to their software architecture.

**Program Files:** This directory is primarily used for 64-bit applications.

**Program Files (x86):** This directory is primarily used for 32-bit applications on 64-bit Windows.

A 64-bit version of Windows can generally run compatible 64-bit and 32-bit applications. Separating their installation directories helps Windows maintain compatibility between applications that use different architectures.

For example, a 64-bit application might be installed in `C:\Program Files`, while a 32-bit application might be installed in `C:\Program Files (x86)`.

This distinction is a convention rather than an absolute rule. Applications can be installed in other directories, and 32-bit versions of Windows generally do not use the same directory separation.

Understanding these folders is useful when locating installed software, investigating application files, or troubleshooting software compatibility issues.

# 2. COMMAND PROMPT AND POWERSHELL

## 2.1 What is the purpose of the command line?

The command line is a text-based interface through which a user interacts with an operating system by entering commands.

Instead of navigating menus and selecting graphical options, users can type instructions to perform tasks such as navigating directories, displaying system information, managing files, and troubleshooting network problems.

For example, entering `hostname` displays the computer's host name. Entering `whoami` displays the identity of the account running the command.

Command-line tools are valuable because they provide direct access to many administrative functions. They can also be used in scripts to automate repetitive tasks.

In cybersecurity, the command line is useful for examining system information, checking network configuration, inspecting running processes, and collecting information during an investigation.

The command line does not automatically grant additional privileges. A command's success depends on the user's permissions, the operating system, and the operation being performed.

## 2.2 What is the difference between Command Prompt and PowerShell?

Command Prompt, commonly called CMD, is a Windows command interpreter designed primarily for traditional Windows commands and batch-file operations.

PowerShell is a more advanced command-line shell and scripting environment designed for system administration and automation.

CMD commonly uses commands such as `dir`, `cd`, and `ipconfig`. Its traditional batch scripts use `.bat` or `.cmd` file extensions.

PowerShell uses cmdlets such as `Get-ChildItem`, `Get-Location`, and `Get-Process`. PowerShell scripts commonly use the `.ps1` extension.

An important difference is how they handle information. CMD generally works with text-based command output, while PowerShell works with structured objects containing properties and methods. This makes it easier to filter, sort, and process information in administrative scripts.

For example, both environments can list files, but CMD uses `dir`, whereas PowerShell provides `Get-ChildItem`.

PowerShell can also run many familiar Windows commands. Some familiar command names, including `dir`, are aliases for PowerShell cmdlets.

Both tools are useful, but PowerShell is particularly valuable when an administrator needs to automate complex tasks or manage multiple Windows systems consistently.

## 2.3 Which command displays the current directory?

In Command Prompt, typing `cd` without specifying another directory displays the current working directory.

In PowerShell, the equivalent cmdlet is `Get-Location`. PowerShell also supports the alias `pwd`.

The current working directory is the directory from which relative file paths and commands are interpreted.

For example, if CMD displays `C:\Users\Student`, the session is currently working in that directory. A command referring to `notes.txt` without a full path will normally look for that file in the current directory.

This command is useful when navigating folders, executing scripts, and troubleshooting situations in which a file cannot be found.

## 2.4 Which command lists files and folders?

In CMD, the command is `dir`.

In PowerShell, the cmdlet is `Get-ChildItem`. The aliases `dir` and `ls` are also available in the standard PowerShell environment.

These commands display the files and directories contained in a specified location. If no path is supplied, they normally display the contents of the current working directory.

For example, `dir C:\Users` lists the entries within the Users directory in CMD.

In PowerShell, `Get-ChildItem C:\Users` performs the corresponding operation.

This command is useful when locating files, examining directory contents, and verifying whether a file exists before performing an administrative task.

## 2.5 Which command displays the current user?

The command `whoami` displays the identity of the account under which the command is running. It works in both CMD and PowerShell.

The output may contain a computer or domain prefix followed by the username.

For example, `COMPUTER01\Student` indicates a local account named Student on a computer named COMPUTER01. A domain account may be displayed with a domain prefix instead.

Knowing the current user is important when troubleshooting access-denied errors because different accounts may have different permissions.

The command can also help administrators verify which identity is being used during a troubleshooting session.

## 2.6 Which command displays the computer name?

The command `hostname` displays the computer's host name. It can be used in both CMD and PowerShell.

Other options include `echo %COMPUTERNAME%` in CMD and `$env:COMPUTERNAME` in PowerShell.

Computer names help distinguish devices within a network or administrative environment. For example, an IT technician investigating a problem on a particular workstation needs to identify the affected computer accurately.

In larger organizations, computer naming conventions can help administrators recognize a device's department, location, or role, although the exact naming system varies by organization.

# 3. LOCAL USERS AND GROUPS

## 3.1 What is the difference between a Standard User and an Administrator?

A Standard User is an account intended for ordinary computing tasks with limited authority over system-wide configuration. An Administrator has additional privileges for managing the computer and performing administrative operations.

A Standard User can generally open applications, create documents, and change many personal settings. However, the account may be prevented from installing software for all users, changing protected system settings, or managing other accounts.

An Administrator can perform a wider range of operations, such as installing many system-wide applications, managing local accounts, and changing security settings. Windows may still require confirmation through User Account Control (UAC).

The distinction is important because excessive administrative privileges increase risk. If an administrator account is compromised, an attacker may gain greater control over the affected system.

Organizations therefore commonly apply the principle of least privilege: users should receive only the access necessary to perform their responsibilities.

## 3.2 What is a user group?

A user group is a collection of user accounts that can be managed together for administrative and access-control purposes.

Instead of assigning identical permissions to every user individually, an administrator can place appropriate accounts into a group and grant permissions to that group.

For example, an organization might create a group for the Human Resources department and grant the group access to an HR document folder.

Windows also includes built-in local groups, such as Administrators and Users. Membership in these groups affects the privileges available to an account.

Groups simplify administration, particularly when employees join a department, change roles, or leave an organization.

However, administrators must review group membership carefully because membership in a privileged group can grant significant access.

## 3.3 Which command lists local user accounts?

The command `net user` displays user accounts in the local-account context when run on a typical standalone Windows computer.

For example, entering `net user` displays the available local account names. Entering `net user Student` displays additional information about the specified account, if it exists and can be queried.

PowerShell also provides the `Get-LocalUser` cmdlet on supported Windows systems.

These commands are useful when verifying whether an account exists, reviewing local account configuration, and troubleshooting account-related problems.

It is important to distinguish local accounts from domain accounts. Domain users are managed through the organization's directory service, and local account-listing commands do not necessarily provide a complete list of domain users.

## 3.4 Which command lists local groups?

The command `net localgroup` displays local groups on a Windows computer.

To display the members of the local Administrators group, an administrator can use `net localgroup Administrators`.

PowerShell also provides the `Get-LocalGroup` cmdlet on supported systems.

These commands are useful for reviewing local group membership and investigating whether accounts have been granted administrative privileges.

For cybersecurity, reviewing privileged group membership can help identify unnecessary access and improve adherence to the principle of least privilege.

## 3.5 Why are permissions important?

Permissions define which actions an account or process is allowed to perform on a resource.

Resources may include files, folders, printers, applications, and system objects. Depending on the resource, permissions can allow users to read information, create or modify content, delete items, or change access settings.

For example, employees may need permission to read a shared company policy document, while only authorized staff should be able to modify it.

Correct permissions protect confidential information, reduce accidental damage, and help prevent unauthorized activity.

Permissions are also important to the three core principles of information security: confidentiality, integrity, and availability.

Confidentiality ensures that information is accessible only to authorized parties. Integrity concerns protecting information from unauthorized alteration. Availability means ensuring that authorized users can access resources when needed.

# 4. ACTIVE DIRECTORY

## 4.1 What is Active Directory?

Active Directory Domain Services (AD DS) is a Microsoft directory service that organizations use to centrally manage identities, computers, groups, and other resources in a traditional Windows domain environment.

It stores information about directory objects and supports domain authentication, directory queries, and centralized administration.

For example, an organization with hundreds of employees can use Active Directory to manage employee accounts and domain-joined computers without treating every account as an unrelated local account.

Active Directory also works with other Windows technologies, including Group Policy, to support consistent administration and security configuration.

From a cybersecurity perspective, Active Directory is important because it often controls access to business systems and resources. Poorly protected privileged accounts or incorrect permissions can create significant security risks.

Active Directory Domain Services should not be confused with Microsoft Entra ID, which is Microsoft's cloud-based identity service. Organizations may use both technologies together.

## 4.2 What is a domain?

In Active Directory, a domain is a logical administrative and security boundary containing directory objects managed through the domain's directory service.

These objects can include user accounts, computer accounts, and groups. Domain administration allows an organization to manage many identities and resources within a shared environment.

For example, a company might use an internal domain such as `ad.example.com`.

A domain account can be used to access authorized domain resources from different domain-joined computers, subject to authentication requirements, permissions, and organizational policies.

A domain simplifies centralized identity management, but it does not automatically grant every domain user access to every resource.

## 4.3 What is a Domain Controller?

A Domain Controller is a server running Active Directory Domain Services that participates in managing and authenticating identities within an Active Directory domain.

It stores a copy of the domain directory and processes relevant directory requests. Domain Controllers also participate in replicating directory changes with other Domain Controllers in the domain.

When an employee signs in using a domain account, the computer uses the configured domain authentication mechanisms to validate the sign-in, often by communicating with an available Domain Controller.

Organizations commonly deploy multiple Domain Controllers to improve availability and resilience.

Domain Controllers are high-value systems because they support essential identity and access-management functions. They require strong security controls, restricted administrative access, and appropriate monitoring.

## 4.4 What is an Organizational Unit (OU)?

An Organizational Unit is a container within an Active Directory domain used to organize directory objects and support delegated administration.

An OU can contain users, computers, groups, and other OUs. Organizations may organize OUs according to departments, locations, administrative responsibilities, or other requirements.

For example, a company might create separate OUs for IT, Finance, and Human Resources.

Administrators can link Group Policy Objects to OUs to apply suitable settings to objects within the policy's scope. They can also delegate selected administrative tasks at the OU level.

An OU is different from a security group. An OU primarily organizes directory objects and supports policy scope and administration, whereas a security group is commonly used to assign permissions to its members.

## 4.5 Why do organizations use Active Directory?

Organizations use Active Directory to simplify identity management, access control, and administration across many computers and users.

Its major benefits include centralized account management, support for domain authentication, group-based access management, directory organization, and integration with Group Policy.

For example, when an employee joins a company, an administrator can create a domain account, place it in appropriate groups, and organize it within the relevant OU. The employee can then receive access to authorized resources according to the organization's configuration.

Centralized administration improves consistency and reduces the need to configure every computer independently.

However, Active Directory must be secured properly. Administrators should protect privileged accounts, restrict unnecessary access, monitor important changes, and keep Domain Controllers appropriately maintained.

# 5. GROUP POLICY

## 5.1 What is a Group Policy Object (GPO)?

A Group Policy Object is a collection of policy settings used to configure supported Windows features and administrative behavior.

GPOs allow administrators to manage settings centrally instead of configuring every computer or user individually.

In an Active Directory environment, a GPO can be linked to a site, domain, or OU. Windows also supports local Group Policy on individual computers.

Policies may control supported security settings, administrative options, user-environment settings, scripts, and other system behavior.

For example, an organization might use Group Policy to establish a consistent security configuration across a set of domain-joined computers.

A GPO does not automatically affect every computer in an organization. Its application depends on its links, scope, security filtering, processing rules, and the configuration of the relevant clients.

## 5.2 What is the difference between Computer Configuration and User Configuration policies?

Computer Configuration contains policy settings that target computers. User Configuration contains policy settings that target user accounts.

Computer Configuration is useful for settings that should apply to a machine regardless of which user signs in, subject to the specific policy's behavior.

User Configuration is useful for settings intended to follow users within the applicable policy scope.

For example, an administrator might configure a computer-wide security setting through Computer Configuration and a supported user-environment setting through User Configuration.

The two sections help administrators separate machine-related requirements from user-related requirements.

The exact effect of a policy depends on the setting itself, the GPO's scope, and the way Windows processes that policy.

## 5.3 Why are GPOs useful in large organizations?

GPOs are useful because they help organizations enforce consistent configurations across large numbers of Windows computers and user accounts.

They reduce repetitive administrative work, support centralized security configuration, and allow different settings to be applied to different organizational areas.

For example, a company may apply one set of policies to ordinary employee workstations and a different set to computers used for administrative duties.

GPOs also help administrators respond to changing requirements. When a policy is appropriately configured and linked, Windows can apply it to the intended scope without requiring the administrator to repeat every configuration step manually.

However, poorly designed policies can cause unexpected restrictions or conflicts. Administrators should test important changes, document policy purposes, and verify the resulting settings.

## 5.4 Which command forces a Group Policy update?

The command is:

`gpupdate /force`

The `gpupdate` utility refreshes Group Policy settings. The `/force` option requests that all applicable policy settings be reapplied, including settings that have not changed.

By default, the command updates both user and computer policy settings. An administrator can target a specific scope with `/target:user` or `/target:computer`.

Some policy changes may require a sign-out or restart before their effects become visible.

Microsoft's documentation explains the command's options and behavior: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/gpupdate

## 5.5 Which command displays the Group Policies applied to a computer?

The command is:

`gpresult /r`

It displays a summary of Resultant Set of Policy information, including applied Group Policy information for the current user and computer.

For a more detailed HTML report, use:

`gpresult /h C:\gp-report.html`

The HTML report can be opened in a browser to examine the available policy results.

This is useful when a policy does not appear to have taken effect. An administrator can inspect the results, confirm the intended policy scope, and investigate possible reasons for a policy not being applied.

The command reports policy results; it does not itself correct a misconfigured GPO.

Microsoft's documentation provides further details: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/gpresult

# 6. WINDOWS EVENT LOGS

## 6.1 What are Windows Event Logs?

Windows Event Logs are records of events generated by the operating system, applications, and other components.

An event may represent a successful operation, a warning, an error, a security-related activity, or another recorded occurrence.

An event entry may contain a timestamp, event source, event ID, severity level, description, and additional diagnostic information.

For example, Windows may record an application failure or a service-startup problem. Security events may also be recorded when the appropriate auditing is configured.

Event Logs help administrators reconstruct activity and identify possible causes of technical problems.

In cybersecurity, logs are important sources of evidence. Nevertheless, they do not record every action on a computer, and the available evidence depends on logging configuration, retention, and system integrity.

## 6.2 Which tool is used to view Windows Event Logs?

The primary graphical tool is Event Viewer.

It can be opened by pressing Windows + R, entering `eventvwr.msc`, and pressing Enter.

Event Viewer allows users to browse logs, filter events, inspect event details, and investigate recorded errors or security-related activity.

Administrators can examine timestamps, event sources, event IDs, and descriptions to understand what happened.

Windows also provides command-line utilities such as `wevtutil` for querying and managing event logs.

Event Viewer is particularly useful during troubleshooting because it provides more context than simply knowing that an application or service failed.

## 6.3 Name the four primary Windows log categories.

The four primary categories under Windows Logs in Event Viewer are Application, Security, System, and Setup.

**Application:** Records events generated by applications and software components. For example, an application may record an error when it fails.

**Security:** Records security auditing events according to the system's auditing configuration. Certain successful and failed sign-in events may appear here when the appropriate auditing is enabled.

**System:** Records events involving Windows system components, services, drivers, and related operating system activities. For example, a service may fail to start.

**Setup:** Records events related to Windows installation, setup, and certain servicing operations.

These categories serve different purposes, so selecting the correct log is important when investigating a problem.

Windows also maintains other logs and application-specific channels beyond these four primary categories.

## 6.4 What is the difference between an Information event and an Error event?

An Information event records an occurrence that Windows or an application considers informational. It may indicate that an operation completed or a service started successfully.

An Error event indicates that a problem or failure occurred during an operation.

For example, an Information event may record a successful service startup, while an Error event may record that the service failed to start.

Other event levels include Warning, Critical, and Verbose, depending on the log and event provider.

The event level alone does not establish the cause or severity of a cybersecurity incident. An Error event does not automatically mean malware is present, and an Information event does not prove that a system is secure.

Administrators should examine the event details and surrounding events before deciding what action to take.

## 6.5 Why are Event Logs useful for troubleshooting and cybersecurity?

Event Logs provide information that helps IT professionals investigate technical failures, monitor system behavior, and examine potential security incidents.

**Troubleshooting:** Application and System logs can help identify software crashes, service failures, and operating system problems.

**Security investigations:** Security logs can help investigators examine account sign-ins and other audited activities.

**Monitoring:** Administrators can review recurring warnings or errors to identify patterns that may indicate a developing problem.

**Incident response:** Timestamps and event details can help investigators establish a timeline of recorded activity and correlate it with other evidence.

**Accountability:** When appropriate auditing is enabled, logs may help establish which account performed a recorded action.

For example, if an employee reports repeated sign-in problems, an administrator can examine relevant security events and compare the timestamps with the reported incidents.

Event Logs have limitations. Records may be incomplete, overwritten, cleared, or unavailable because of configuration issues. Therefore, investigators should correlate logs with other evidence instead of relying on a single event.

# 7. PRACTICAL APPLICATION: HOW THE CONCEPTS WORK TOGETHER

Consider an organization in which an employee cannot access a shared folder, and a required security policy does not appear to be active.

An IT administrator could approach the situation systematically.

First, the administrator would identify the affected computer using `hostname` and verify the account using `whoami`.

Second, the administrator would examine the user's permissions and group membership to determine whether the account should have access to the folder.

Third, if the computer is domain-joined, the administrator could verify the relevant Active Directory account, group membership, and OU placement.

Fourth, the administrator could run `gpresult /r` to inspect the Group Policy results and determine whether the expected policy appears to have been applied.

Fifth, the administrator could use `gpupdate /force` to request a policy refresh, then verify the result. If the problem remains, the administrator could examine relevant event logs and policy-processing errors.

Finally, the administrator would document the findings and apply an appropriate correction based on the evidence.

This example demonstrates that Windows administration is not simply about memorizing commands. It requires identifying the problem, gathering evidence, understanding permissions and policies, and verifying whether the solution works.

# Conclusion

Windows fundamentals provide the foundation for effective IT support, system administration, and cybersecurity. Understanding the file system helps administrators locate and protect information. Command-line tools make it easier to inspect and manage computers. Local users, groups, and permissions establish access boundaries, while Active Directory supports centralized identity management in domain environments.

Group Policy helps organizations maintain consistent configurations, and Windows Event Logs provide records that assist with troubleshooting and security investigations.

These components work together to help organizations maintain reliable, manageable, and secure Windows environments. Developing a strong understanding of them is an important step toward more advanced topics in Windows administration and cybersecurity.

# References

1. Microsoft Learn — `gpupdate` command: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/gpupdate
2. Microsoft Learn — `gpresult` command: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/gpresult
3. Microsoft Learn — Applying Group Policy troubleshooting guidance: https://learn.microsoft.com/en-us/troubleshoot/windows-server/group-policy/applying-group-policy-troubleshooting-guidance

*Submission note: Review the explanations, adjust the wording to reflect your own understanding, and follow any formatting or referencing instructions provided by your instructor.*
