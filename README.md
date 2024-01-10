# XenonStack Project

## Custom Linux Command

We are going to create a shell script for linux to create a custom command for making the process simpler and less time-consuming. 

## Overview

`internsctl` is a custom Linux command designed to streamline server operations. It provides functionalities to retrieve CPU and memory information, create new users, and list existing users on the server.

## Getting Started

### Installation

Clone the repository:

```bash
git clone https://github.com/your-username/internsctl.git
cd internsctl
```

The code used to create this custom linux command is:

```bash
#!/bin/bash

# internsctl - A custom command for managing server operations

VERSION="v0.1.0"

function show_help() {
    echo "Usage: internsctl [OPTION]... [SUBCOMMAND]"
    echo "..."
    # Add more help information as needed
}

function show_version() {
    echo "internsctl version $VERSION"
}

# Parse command line arguments
case "$1" in
    -h|--help)
        show_help
        ;;
    -v|--version)
        show_version
        ;;
    cpu)
        # Handle CPU commands
        if [ "$2" == "getinfo" ]; then
            # Code to get CPU information
            lscpu
        else
            echo "Unknown CPU command: $2"
            exit 1
        fi
        ;;
    memory)
        # Handle memory commands
        if [ "$2" == "getinfo" ]; then
            # Code to get memory information
            free
        else
            echo "Unknown memory command: $2"
            exit 1
        fi
        ;;
    user)
        # Handle user commands
        case "$2" in
            create)
                # Code to create a new user
                # Usage: internsctl user create <username>
                ;;
            list)
                # Code to list users
                if [ "$3" == "--sudo-only" ]; then
                    # Code to list users with sudo permissions
                    ;;
                else
                    # Code to list all regular users
                    ;;
                fi
                ;;
            *)
                echo "Unknown user command: $2"
                exit 1
                ;;
        esac
        ;;
    *)
        echo "Unknown option or subcommand: $1"
        echo "Try 'internsctl --help' for more information."
        exit 1
        ;;
esac

exit 0
```

## Usage 

### Manual
Execute the following command to view the full documentation of 'internsctl':
```bash
man internsctl
```

### Help
To understand the use cases with examples, use the following command:
```bash
internsctl --help
```

### Version Information
To check the version of 'internsctl', use:
```bash
internsctl --version
```

### Get CPU Information
Execute the following command to get CPU information:
```bash
internsctl cpu getinfo
```

### Get Memory Information
Execute the following command to get memory information:
```bash
internsctl memory getinfo
```

### Create a New User
To create a new user with login access and a home directory, use:
```bash
internsctl user create <username>
```

###List All Regular Users
To list all regular users on the server, use:
```bash
internsctl user list
```

###List Users with sudo Permissions
To list all users with sudo permissions, use:
```bash
internsctl user list --sudo-only
```

