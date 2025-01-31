# Get Next Line Project

## Description
The `get_next_line` project is an implementation of a function that reads a line from a file descriptor, handling multiple file descriptors efficiently. This function ensures that each call retrieves the next line until the end of the file is reached.

## Features
- Reads a line from a given file descriptor.
- Manages multiple file descriptors simultaneously.
- Handles memory efficiently to avoid leaks.
- Works with any type of file descriptor, including standard input.

## Function Prototype
```c
char *get_next_line(int fd);
```

## Implementation Details
- Uses a static buffer to store read data efficiently.
- Implements a loop to read from the file descriptor until a newline or EOF is found.
- Uses dynamic memory allocation to store lines progressively.

## Usage
### Clone the Project
```sh
git clone https://github.com/Nalveiz/get_next_line
cd get_next_line
```

### Compilation
Compile the function with your program using:
```sh
gcc -Wall -Wextra -Werror get_next_line.c get_next_line_utils.c get_next_line.h main.c
```

### Example Usage
```c
#include <fcntl.h>
#include <stdio.h>
#include "get_next_line.h"

int main(void)
{
    int fd = open("test.txt", O_RDONLY);
    char *line;
    while ((line = get_next_line(fd)))
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

## Notes
- Ensure `BUFFER_SIZE` is defined for optimal performance.
- Free the returned string after use to prevent memory leaks.

## License
This project is open-source and free to use.
