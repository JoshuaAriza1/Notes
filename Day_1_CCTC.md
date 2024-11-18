C:\> 
PowerShell is not case sens
when using quotes it will look for something spec
get-Process 
Get-Help for issues and will display option for the issue
Get-verb
Get-variable
Get-COntent
Get-COmmand
Stop-service
Get-service
Get-History
Get-Alias
Get-Alias Dir
Power\shell properties
Everything in power shell is an object
Get-Member will list all poroperty and methods
Website for notes https://os.cybbh.io/public
Get-process | Get-member
.property
.name
Start-Process calc will open an instance of a calc
Get-Content -Path "C:\Test Files\content.txt"                                         # Displays the contents of the file
Get-Variable                                                                          # Displays current Variables
Get-Verb                                                                              # List the PowerShell verbs
Get-Command                                                                           # List the PowerShell cmdlets
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun    # Get cmdlets and display them in order
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility       # Get commands in a module
Get-Help <cmdlet>                                                 # Displays help about a PowerShell cmdlet
Get-Help get-process                                              # Displays help for Get-Process cmdlet
Get-Help get-process -online                                      # Opens a web browser and displays help for the Get-Process cmdlet on the Microsoft website
Get-History <like Linux will return previous entered commands.>   # Displays history of commands in current window
Get-Location <similar to PWD on Linux, gl is the alias.>          # Displays present working directory
Get-Help about_command_syntax                                     # Displays help about command syntax
et-Alias <alias>                                                 # Displays aliases for a given command name
Get-Alias dir                                                     # Returns Get-ChildItem
Get-Process | Get-Member                       # Gives the methods and properties of the object/cmdlet
(cmdlet).property                              # Command Structure
(Get-Process).Name                             # Returns the single property of 'name' of every process
Start-Process Notepad.exe                      # This cmdlet uses the Process.Start Method of the System.Diagnostics.Process class to open notepad.exe
Stop-Process -name notepad                           # This cmdlet uses the Process.Kill Method of the System.Diagnostics.Process class to stop notepad.exe
Get-Process | Select-Object Name, ID, path     # Displays the Get-Process Properties of 'Name, ID, Path' for every process
Get-Help Format-Table
Get-Help Format-List
Get-Process | Get-Member | Where-Object {$_.Membertype -match "Method"}       # Displays all objects with Method in their name from the results from Get-Member of the Get-Process cmdlet
Start-Process calc                              # Open an instance of calculator
(Get-Process calculator*).kill()                # Stops a named process using the kill() method directly
Stop-Process -name calculator*                  # Uses a cmdlet to call the Process.Kill method
Get-Process | Select-Object Name, ID, path | Where-object {$_.ID -lt '1000'}            # List all the processes with a PID lower than 1000
(Get-Process | Select-Object Name, ID, path | Where-object {$_.ID -lt '1000'}).count    # List all the processes with a PID lower than 1000
Get-LocalUser | Get-Member      # Displays Properties and Methods of Get-LocalUser cmdlet
Get-Cimclass *                                                                  # Lists all CIM Classes
Get-CimInstance –Namespace root\securitycenter2 –ClassName antispywareproduct   # Lists the antispywareproduct class from the root/security instance
Get-CimInstance -ClassName Win32_LogicalDisk -Filter “DriveType=3” | gm         # Shows properties and methods for this Instance
Get-WmiObject -Class Win32_LogicalDisk -Filter “DriveType=3”     # Using the Windows Management Instrumentation method
CimInstance is the OS default
Get-CimInstance -class Win32_BIOS                      # Queries Win32_Bios
Get-WmiObject -Class Win32_BIOS                        # same output but deprecated command
Get-Help about_For
Get-Help about_Foreach
Get-Help about_While
Get-Help about_Do
do {<statement list>} while (<condition>)
do {<statement list>} until (<condition>)
Get-Variable                      # Names are displayed without the preceding <$>
Clear-Variable -Name MyVariable   # Delete the value of a Variable
Remove-Variable -Name MyVariable  # Delete the Variable
MyVariable = 1, 2, 3             # Creates the MyVariable with 1,2,3
$Processes = Get-Process          # Creates a Variable with the results of Get-Process
$Today = (Get-Date).DateTime      # Creates a combined Date/Time variable from the results of Get-Date


$PSHome | Get-Member              # Displays System.String with it's objects and properties
$A=12                             # Creating A with an integer
$A | Get-Member                   # Displays System.Int32

Get-Help about_Functions                                      # Displays the help about Functions
Get-Help about_Functions_Advanced                             # Displays some more in-depth help about Functions
Function Do-Stuff { Get-Date; Get-Process; Get-Service }      # Creates a Function with 'Get-Date, Get-Process, Get-Service' inside of it
Do-Stuff                                                      # Runs the Function
Get-ExecutionPolicy -list                                             # Lists all of the Scopes and ExecutionPolicies on the system
Get-ExecutionPolicy                                                   # Gets the current user's ExecutionPolicy
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser  # Sets the ExecutionPolicy for the CurrentUser to Unrestricted

comparison Op
-lt ess than

-le Less than or equal to

-gt Greater than

-ge Greater than or equal to

-eq Equal to

-ne Not equal to

-like Like (uses wildcard for pattern matching)

-match A match using Regular Expressions
Powershell Profiles are location for presistance 
.ps1 are executiable
All Users, All Hosts $PsHome\Profile.ps1

All Users, Current Host $PsHome\Microsoft.PowerShell_profile.ps1

Current User, All Hosts $Home\[My]Documents\Profile.ps1

Current User, Current Host $Home\[My ]Documents\WindowsPowerShell\Profile.ps1
$PsHome         # Stores the installation directory for PowerShell
$Home           # Stores the current user’s home directory
$profile | Get-Member -Type NoteProperty                        # Displays the profile values of Names, MemberType, and Paths.
$Profile | get-member -type noteproperty | ft -wrap             # Displays the same results but completed in case it was cut off '...'
$PROFILE | Get-Member -MemberType noteproperty | select name    # Narrowed results to display only Names
Get-PSSessionConfiguration
