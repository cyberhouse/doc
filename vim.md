# How-Tos
## Write Changes as Root (`sudo` Required)

    :w !sudo tee %

## Add 23 to the Number in Column 42

    %s/\%42\d\+/\=submatch(0) + 23

## Use Vimdiff to Compare Remote Files

    vimdiff scp://host1//etc/passwd scp://host2//etc/passwd

## Change Tab/Space Behaviour

Display unprintable characters
    :set list
Use spaces instead of tabs
    :set expandtab
Length of an Tab
    :set tabstop=4
Number of spaces used for (auto)indent.
    :set shiftwidth=4
Apply settings to existing text
    :retab

## Set Current Direcory to the one of the File Currently Open

    :cd %:p:h

<!---
 vim: expandtab tabstop=4 shiftwidth=4
-->
