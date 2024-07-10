# NetTool

NetTool is a Python-based network utility for listening to incoming connections, executing commands, initializing a command shell, and uploading files to specified destinations. Ideal for penetration testing and network troubleshooting.

## Features

- **Listen Mode:** Listen on a specified host and port for incoming connections.
- **Execute Command:** Execute a specified file upon receiving a connection.
- **Command Shell:** Initialize a command shell for interactive command execution.
- **File Upload:** Upload a file to a specified destination upon receiving a connection.

## Usage

To use Net Tool, run the `netTool.py` script with the appropriate options. Below are the available options and their descriptions:
Usage: python3 netTool.py -t target_host -p port
-l --listen - Listen on [host]:[port] for incoming connections
-e --execute=file_to_run - Execute the given file upon receiving a connection
-c --command - Initialize a command shell
-u --upload=destination - Upon receiving connection, upload a file and write to [destination]


### Examples

1. **Initialize a command shell:**
   ```bash
   python3 netTool.py -t 192.168.0.1 -p 5555 -l -c
2. **Upload a file to a specified destination:**
   ```bash
   python3 netTool.py -t 192.168.0.1 -p 5555 -l -u=c:\\target.exe
3. **Execute a command upon receiving a connection:**
   ```bash
   python3 netTool.py -t 192.168.0.1 -p 5555 -l -e="cat /etc/passwd"
4. **Send data to a target host:**
   ```bash
   echo 'ABCDEFGHI' | python3 netTool.py -t 192.168.11.12 -p 135

## Installation
To use Net Tool, ensure you have Python 3 installed on your system. Clone the repository and navigate to the directory containing the script.

git clone https://github.com/yourusername/netTool.git
cd netTool

## How it works
**Client-Side Operation**
The `client_sender` function connects to the target host and port, sends data, and waits for a response. It operates in a loop, allowing continuous data exchange between the client and server.

**Server-Side Operation**
The `server_loop` function sets up a server to listen for incoming connections. Upon accepting a connection, it spawns a new thread to handle the client using the `client_handler` function.

**Command Execution**
The `run_command` function executes system commands and returns the output. It is used by the server to execute commands received from the client.

**File Upload**
The `client_handler` function handles file uploads by reading incoming data and writing it to the specified destination.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request with your improvements.

## License
This project is licensed under the MIT License.
