# EGO

A bare bones cross-platform terminal based text editor written in Go<br>

# Screenshot

![IMAGE ALT TEXT HERE](https://raw.githubusercontent.com/maksimKorzh/ego/main/assets/ego.png)

# Features

- modes (VIEW/EDIT)
- display buffer & status bar
- inserting characters
- deleting characters
- concatenating lines
- inserting lines
- deleting lines
- navigation
- copy/paste
- undo/redo
- syntax highlighting
- search/replace(GNUsed as plugin)

# Key bindigns

       ESC: enter the 'VIEW' mode
         e: enter the 'EDIT' mode
         q: quit from the text editor
         w: write file to disk
         a: cat current line to previous one
         d: cut current line to copy buffer
         c: copy current line to copy buffer
         p: paste line from copy buffer
         s: push text buffer to undo buffer
         l: pull text buffer from undo buffer
         h: toggle syntax highlighting
         x: execute GNUsed command
       0-9: navigate throughout the file
    Arrows: move cursor
    PgDown: scroll 1/4 of the screen downwards
      PgUp: scroll 1/4 of the screen upwards
      HOME: move cursor to the begining of the current line
       END: move cursor to the end of the current line

# GNUsed cheat sheet

    Search:

    /hello/=              # puts cursor on the line where first occurrence of "hello" is found
    10,20 {/hello/=}      # same as above but within lines 10-20
    10,$ {/hello/=}       # same as above but from line 10 to the end of document


    Replace:

    s/hello/hi/g          # replace "hello" with "hi" in the entire document
    10 s/hello/hi/        # same but only on line 10
    10,20 s/^/    /       # set indentation 4 spaces within the lines 10-20
    s/ *$//g              # remove trailing spaces entire document

    Move:

    1,10d                 # delete lines 1-10
    1,10H; 11g            # copy lines 1-10 and paste to line 11
    1,10H; 11g 1,10d      # cut lines 1-10 and paste to line 11

    NOTE: to use GNUsed on Windows you need first to install it and make
          sure 'sed.exe' utility is available system wide, you can find
          the windows installer file in this repo in a folder 'sed'.

# Usage

    $ ego                 # opens editor with 'out.txt' source file name
    $ ego my_file.txt     # opens editor with 'my_file.txt' if it exists,
                          # otherwise sets source filename to 'my_file.txt'

# Build from sources

```bash
cd src
go mod init ego
go build -o ego e.go
```
