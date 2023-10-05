# Features

Program accepts any `.txt` or `.md` file or a folder/directory of `.txt`/`.md` files and converts them to .html files for use in webpages. 

HTML files consist of `<p>` tags for text and `<br/>` for spaces from text. 

Will also process markdown file features including `<h1>`, `<h2>` for titles, `<strong>` and `<em>` for bold and italics, and `<a>` for links

Also will create a `<title>` and `<h1>` out of the first line in a text file if it is followed by 2 new lines.

Allows for user to specify output folder for HTML files generated by the program. If specified folder doesn't exist a new temp one will be created.

# How to Run 

**In command line:**

Make sure python is installed:

`$ python --version`

Clone the Repo

```
$ git clone https://github.com/ijacobs-cpa/textml.git
$ cd textml/ 
```

run the program 

`$ python textml.py <options> `

or

`$ python textml.py [file/directory] <commands> [command argument]`

## Command Flags

| Command   | Description |
| --------- | ----------- |
| -v, --version | Displays version of the program |
| -h, --help | Displays a help message |
| -o, --output [location] | Specifies the location to save converted files, creates a new folder if location doesn't exist, defaults to textml/ |
| -l, --lang [language-code] | Specifies a language for the <html lang=...> element in the <html> root element |
| -c, --config [options-configuration] | Specifies all the options in a TOML formatted configuration file instead of having to pass them all as command line arguments every time. |

## Examples

Converting a file:

`$ python textml.py myfile.txt`

Converting all files in a directory:

`$ python textml.py mydirectory/`

Running Commands:

`$ python textml.py -v`

Specifing Output Directory:

`$ python textml.py myFile.txt -o newDir/`

Processing Markdown File : 

`$ python textml.py mdtest.md`

Specifing multiple arguments:

`$ python textml.py myFile.txt -o newDir/ --lang en-US`

## File Examples

Here is an example of a text file being converted from the examples folder (examples/liveTest):

Command:

`$ python textml.py examples/liveTest/index.txt -o examples/liveTest/`

Initial text file:
```
Today I learned


Documenting some information I've learned today

Here is some information:


6502 Assembly Notes (KEY_terms):

#{number} adds a nuber
${hex} adds a hexadecimal

LDA = Load the accumulator

LDY = Load the Y register
LDX = Load the X register

STA = Store the accumulator
STY = Store the Y register
STX = Store the X register

CPX = compare THE x register
```
```HTML
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Today I learned</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
<body>
<h1>Today I learned</h1>
  <br />
  <p>Documenting some information I've learned today</p>
  <br />
  <p>Here is some information:</p>
  <br />
  <p>6502 Assembly Notes (KEY_terms):</p>
  <br />
  <p>#{number} adds a nuber</p>
  <p>${hex} adds a hexadecimal</p>
  <br />
  <p>LDA = Load the accumulator</p>
  <br />
  <p>LDY = Load the Y register</p>
  <p>LDX = Load the X register</p>
  <br />
  <p>STA = Store the accumulator</p>
  <p>STY = Store the Y register</p>
  <p>STX = Store the X register</p>
  <br />
  <p>CPX = compare THE x register</p>
  <br />
</body>
</html>
```

# Changelog

**0.1.7**
- Added Optional HTML file Language specification
    - Updates the `<html lang=...>` attribute in the root `<html>` element. If no language is provided `en-CA` is used by default.
- Added conversion of `---` to `<hr/>` in markdown files 

**0.1.6:** (Based on Feedback)
- Updated argument handling to use argparse
- Simplified directory deletion using shutil
- Normalized working with paths by utilizing os.path functions (instead of strings)
- Refactored title parsing code
- Modularized program's convert functions into its own file [*convertUtils.py*](https://github.com/ijacobs-cpa/textml/blob/main/convertUtils.py)

0.1.5: (merged pull request from [rabroldan](https://github.com/rabroldan))
- Added **Markdown file support**
    -  Markdown syntax features, such as italics, bold, headings (Heading 1 and Heading 2), and links. 
    - Can correctly format these elements when converting Markdown to HTML. 
    - If you specify a single Markdown file it processes that file and saves the HTML output in the "textml" directory. 
    - If you run the script with a directory path it processes any Markdown files and text files within that directory and saves the generated HTML files in the "textml" directory or other specified directory.

0.1.4:
- Added Feature: *Custom Output*
    - Allows user to specify an output location for processed HTML files (Refer to How to Install for running instructions)
    - Creates new location if provided location doesnt exist
- Code Reformatting part 1
- Renamed main file to textml.py
- Fixed parent directories not properly being handled when provided
- No longer ends program when file in folder is not supported (keeps looking for txt files)

0.1.3:

- Now accepts folders passed without a "/"
- Added feature: *Title parsing*
    - Updates `<title></title>` & creates `<h1></h1>` based on title in txt document (title must be in the first line and have 2 newlines right after)
- Reduced amount of `<br/>` lines created to only 1 per newline

0.1.2:

- Updated help message
- Improved the defaultDirSetup() to accept custom directories for future features

0.1.1 - Fixed an Issue with relative filenames

0.1.0 - Initial Commit of project 

# License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)




