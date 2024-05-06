# USB Device Event Handler

This C program demonstrates how to create a simple USB device event handler using Windows Management Instrumentation (WMI) in C. The program listens for USB device insertion and removal events and performs specific actions based on the detected events.

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

## Disclaimer

This program is provided as-is and may need modifications to fit specific requirements or environments. Ensure proper permissions and test thoroughly before deploying it in a production environment.
