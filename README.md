# Client-Server File Transfer System

## Overview

This project implements a robust client-server application designed to efficiently and securely transfer files across a network. It leverages multi-threading on the server-side to handle multiple clients simultaneously while ensuring data integrity and security.

## Features

### 1. Client Program
- Connects to the server via a UNIX domain socket.
- Transmits file transfer requests in a formatted string: `fileName:directory:username:groupname`.
- Receives and displays the server's response regarding the success or failure of the transfer.

### 2. Server Program
- Listens for incoming connections through a UNIX domain socket.
- Processes file transfer requests in a multi-threaded environment.
- Logs session details and file transfer activities.
- Ensures that file transfers are performed with appropriate permissions based on user and group information.

### 3. Multithreaded Connections
- Handles multiple client connections simultaneously by creating a new thread for each client.
- Utilizes `pthread_create` for thread creation and `pthread_detach` to manage thread resources efficiently.

### 4. File Transfer

#### Client-Side Operations
- Collects file name, directory, username, and group information.
- Sends this information to the server as a formatted string.

#### Server-Side Operations
- Parses the received string and constructs file paths.
- Sets effective user and group IDs to ensure proper permissions.
- Reads data from the source file and writes it to the destination file.
- Sends a success or error message back to the client based on the transfer outcome.

### 5. Transfer Authentication
- Uses UNIX user and group IDs to ensure that only authorized users can access their department directories.
- Sets directory permissions to restrict access based on group membership.
- Verifies user permissions before initiating file transfers.

### 6. Synchronisation
- Ensures consistency and allows simultaneous file backups by handling each client on a separate thread.
- Utilizes mutexes to prevent race conditions during read and write operations.

## Conclusion

This client-server application serves as a dependable tool for any organization looking to streamline their data-backup process. By validating users and ensuring appropriate security mechanisms, it provides a high level of data integrity and security.

## Demo

A video demonstration of the system can be found [here](https://youtu.be/JxxL3uvw6_A).
