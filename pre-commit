#!/bin/bash
# Author: Remigijus Jarmalavičius <remigijus@jarmalavicius.lt> 
# Author: Vytautas Povilaitis <php-checker@vytux.lt>

ROOT_DIR="$(pwd)/"
LIST=$(git status | grep -e '\#.*\(modified\|added\)')
ERRORS_BUFFER=""
for file in $LIST
do
    if [ "$file" == '#' ]; then
        continue
    fi
    if [ $(echo "$file" | grep 'modified') ]; then
        FILE_ACTION="modified"
    elif [ $(echo "$file" | grep 'added') ]; then
        FILE_ACTION="added"
    else 
        EXTENSION=$(echo "$file" | grep ".php$")
        if [ "$EXTENSION" != "" ]; then
            echo "Checking $FILE_ACTION file: $file" 
            ERRORS=$(php -l $ROOT_DIR$file 2>&1 | grep "Parse error")
            if [ "$ERRORS" != "" ]; then
                if [ "$ERRORS_BUFFER" != "" ]; then
                    ERRORS_BUFFER="$ERRORS_BUFFER\n$ERRORS"
                else
                    ERRORS_BUFFER="$ERRORS"
                fi
                echo "Syntax errors found in file: $file "
            fi
        fi
    fi
done
if [ "$ERRORS_BUFFER" != "" ]; then
    echo 
    echo "These errors were found in try-to-commit files: "
    echo -e $ERRORS_BUFFER
    echo 
    echo "Can't commit, fix errors first."
    exit 1
else
    echo "Commited successfully."
fi
