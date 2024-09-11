# lsdyna_for_intel_mpi
To create dedicated submit scripts with Intel MPI platform for five specific .
To create dedicated submit scripts with Intel MPI platform for five specific dyna versions.
Overview: - This script automates the process of running LS-DYNA simulations and compressing the output using femzip_dyna. It provides a menu to select the LS-DYNA version, validates user inputs, and logs the process. Dyna submits script for use specific Intel MPI for specific dyna versions.
Current scenario: -
•	Normally there is universal submission script for all dyna versions with Platform MPI by default.
•	But business asked for 5x versions of Dyna with Intel MPI.
•	And where not able to implement / modify existing submission script due to these Intel MPI.
Dynasub for platform_mpi: -
•	Location: - /usr/local/bin/dynasub 
•	Dynasub submission script for all dyna versions with Platform MPI.
Dyna_intel_12.sh for Intel_mpi: -
•	Location: - /soft/intelmpiscripts/dyna_intel_12.sh.
•	dyna_intel_12.sh submission script for 5x dyna versions with Intel MPI.
•	Dyna intel mpi version.
 1.R12.4510_0-dmp-sngl/sngl/lsdyna
 2. R12.4510.0-dmp-dble/dble/lsdyna
 3. R12.2.206-dmp-sngl/sngl/lsdyna
 4. R12.2.206-dmp-dble/dble/lsdyna
 5. R12.4544-dmp-sngl/sngl/lsdyna
Requirement: -
•	Create dedicated submit script that will use specific Intel MPI for those specific dyna versions.
•	Also add femzip option to create zip d3plots files.
Prerequisites: - 
Before running the script, ensure the following software and environment variables are correctly set up:
1.	LS-DYNA: Ensure LS-DYNA is installed, and the executable paths are correctly set in the script.
2.	MPI: Ensure MPI is installed and the mpirun command is available.
3.	femzip_dyna: Ensure femzip_dyna is installed, and the environment variables are set correctly .
Algorithm of code: -
Functions
is_positive_integer()
•	Purpose: Validates if a given string is a positive integer.
•	Parameters:
o	value: The string to validate.
•	Returns:
o	0 if the string is a valid positive integer.
o	1 if the string is not a valid positive integer.
process_file()
•	Purpose: Processes the input file, runs the LS-DYNA simulation, and compresses the output.
•	Steps:
1.	Clears the terminal screen.
2.	Generates a timestamp for the log file name.
3.	Prompts the user to select the LS-DYNA version.
4.	Validates the selected LS-DYNA executable path.
5.	Lists available .dyn files in the current directory.
6.	Prompts the user to enter the path to the LS-DYNA input file.
7.	Validates the input file path.
8.	Prompts the user to enter the number of CPUs to use.
9.	Validates the number of CPUs.
10.	Sets the LSTC_LICENSE_SERVER environment variable.
11.	Runs the LS-DYNA simulation using mpirun.
12.	Compresses the output using femzip_dyna.
Environment Variables: -
•	LSTC_LICENSE_SERVER: - Set to the LS-DYNA license server.
•	SIDACT_LICENSE_FILE: - Set to the SIDACT license file.
•	LD_LIBRARY_PATH: - Set to include the path to the femzip_dyna library.
Usage: -
1.	Run the Script: Execute the script using the following command:
2.	dyna_intel_12.sh
3.	Select LS-DYNA Version: The script will prompt you to select the LS-DYNA version. Enter the corresponding number from the list provided.
4.	Enter Input File Path: The script will list available .dyn files in the current directory. Enter the path to the LS-DYNA input file.
5.	Enter Number of CPUs: Enter the number of CPUs to use for the simulation. The script will validate that the input is a positive integer.
6.	Run Simulation: The script will run the LS-DYNA simulation using the specified parameters and log the output to a file named ls-dyna_run_<timestamp>.log.
7.	Compression: After the simulation completes, the script will compress the output using femzip_dyna and log the process.


