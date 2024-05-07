# USB Device Event Handler

## Description

The USB Device Event Handler program outlines a system login process that utilizes a USB device for user authentication. Here's a breakdown of the process:

1. **USB Insertion**:
   - The process begins when a USB device is inserted into the system.

2. **Check USB Device**:
   - The system verifies if the inserted USB device is the specific USB device designated for user authentication.

3. **Specific USB Detected**:
   - If the inserted USB device matches the specific USB device, the default user currently logged into the system is logged out.
   - Subsequently, the system proceeds to log in the specific user associated with the detected USB device.

4. **Default Session Resumption**:
   - If the inserted USB device does not match the specific USB device, the system resumes the default user session without any changes.

5. **User Logged In**:
   - Once the specific user (presumably associated with the inserted USB device) is logged in, the system monitors for USB removal.

6. **USB Removal Check**:
   - The system continuously checks if the USB device is removed from the system.

7. **USB Removed**:
   - If the USB device is removed, indicating that the user has removed their authentication token, the specific user is logged out.
   - Following this, the system logs in the default user, returning the system to its initial state.

8. **Process Continues**:
   - The process continues to monitor USB insertion and removal events, repeating the authentication and user login/logout cycle as necessary.

This flowchart suggests a security application where a USB key serves as a form of two-factor authentication, allowing access to a specific user account only when the corresponding USB device is present. This approach enhances system security by requiring both a password and physical possession of the USB device for user authentication.

## Dependencies

To compile and run this program, you need:

- Windows operating system
- Visual Studio or another C compiler for Windows
- Windows Driver Kit (WDK) for the required header files and libraries

## Overview

The program performs the following tasks:

1. Initializes COM library.
2. Connects to the local WMI namespace.
3. Sets security on the proxy.
4. Creates an unsecured apartment.
5. Creates a sink for event notifications.
6. Requests notification for USB device insertion/removal events.
7. Listens for events until the user exits.
8. Cleans up resources before exiting.

## How It Works

- The program defines functions for specific actions to be taken when USB events occur, such as logging in/out users.
- It defines a WMI event handler struct and implements its functions to handle event notifications.
- Event notifications are received asynchronously using `ExecNotificationQueryAsync`.
- When a USB event occurs, the corresponding action functions are called based on the event type.

## Usage

1. Compile the program using a C compiler.
2. Run the compiled executable.
3. The program will start listening for USB device events.
4. Plug in or remove USB devices to trigger events.
5. Press Enter to exit the program.

## Remaining Work

The README should include:

- Code snippets for specific functions (if not already provided).
- Instructions on how to compile the program.
- Any additional usage details or considerations.
- Acknowledgment of external libraries or code references (if applicable).

## Remaining Code to Write

1. Implementation of specific action functions (e.g., `LogoutDefaultUser`, `LoginSpecificUser`, etc.).
2. Code snippets for the WMI event handler struct and its functions.
3. Instructions for compiling the program with necessary dependencies.

## Disclaimer

This program is provided as-is and may need modifications to fit specific requirements or environments. Ensure proper permissions and test thoroughly before deploying it in a production environment.
