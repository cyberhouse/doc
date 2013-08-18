# Shell Scripting

## Check for Existence of Binary

    function require_curl() { which "curl" &>/dev/null; }

## Simple Debug Messages

    function debug() { ((DEBUG)) && echo ">>> $*"; }
    ...
    debug "Starting database import."

## Using Default Value if None Provided

    URL=${URL:-http://localhost:8080}

# Tips

- Use hashtags for commands to easily find them again in your history.

# How-Tos
## Run Command Line Editor

    <ESC> e

## Place Argument of Last Command

    <ESC> .
   
## Repairing a Broken Terminal

    reset

## Expand Path to Command

    ls -l =curl

## Paste Todays Date (grml Config) 

    <C-e>d

## Batch Rename File Extension

    zmv -Q '(**/)(*).txt' '$1$2.md'

<!---
 vim: expandtab tabstop=4 shiftwidth=4
-->
   

