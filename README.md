# Bash_cheatsheet
Useful tricks I always needs, I'm always searching and finding them hours after...


# Bash shell in OSX:

### Add newlines after a pattern

    sed 's/XXX/XXX\'$'\n/g' file > file_02
ex:
    sed 's/Control_3_30c/Control_3_30c\'$'\n/g' file > file_02

### Add a line a the top of a file, with tabulation within:

    sed $'1s/^/ZZZa\tYYYb\tXXX/' file > file_02
ex:
    sed $'1s/^/Acclimation_1_31_5a\tAcclimation_1_31_5b\tAcclimation_1_31_5c\tAcclimation_3_30a\tAcclimation_3_30b\tAcclimation_3_30c\tControl_1_30a\tControl_1_30b\tControl_1_30c\tControl_3_30a\tControl_3_30b\tControl_3_30c/' file > file_02
