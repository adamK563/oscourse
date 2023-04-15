# oscourse

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <sys/wait.h>

#define MAX_INPUT_LENGTH 1024

char* read_input() {
    char* input = malloc(sizeof(char) * MAX_INPUT_LENGTH);
    fgets(input, MAX_INPUT_LENGTH, stdin);
    input[strcspn(input, "\n")] = '\0'; // Remove newline character
    return input;
}

int execute_command(char* command, char** path_dirs) {
    char* token = strtok(command, " ");
    char* args[MAX_INPUT_LENGTH / 2];
    int i = 0;
    while (token != NULL) {
        args[i] = token;
        token = strtok(NULL, " ");
        i++;
    }
    args[i] = NULL;

    int pid = fork();
    if (pid == 0) {
        // Child process
        for (int j = 0; path_dirs[j] != NULL; j++) {
            char path[MAX_INPUT_LENGTH];
            sprintf(path, "%s/%s", path_dirs[j], args[0]);
            execv(path, args);
        }
        // If execv() fails, print error message and exit
        printf("Command not found: %s\n", args[0]);
        exit(0);
    } else if (pid < 0) {
        // Fork failed, print error message
        printf("Fork failed\n");
    } else {
        // Parent process, wait for child to finish
        wait(NULL);
    }

    return 1;
}

int main() {
    char* path = getenv("PATH");
    char* path_dirs[MAX_INPUT_LENGTH / 2];
    char* token = strtok(path, ":");
    int i = 0;
    while (token != NULL) {
        path_dirs[i] = token;
        token = strtok(NULL, ":");
        i++;
    }
    path_dirs[i] = NULL;

    while (1) {
        printf("> ");
        char* input = read_input();
        if (strcmp(input, "leave") == 0) {
            free(input);
            break;
        }
        execute_command(input, path_dirs);
        free(input);
    }

    return 0;
}
