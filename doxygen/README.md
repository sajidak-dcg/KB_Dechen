# Set up Doxygen stack

Steps to setup the full Doxygen stack on windows
and to generate documentation for a project

## Folders
These Folders/Locations/Paths will be unique to your installation, and care should be taken to ensure all placeholder replacements are accurately done  
-	Download Path - `<download-path` - refers to location where downloaded binaries are saved
-	Installation Path - `<install-path>` - refers to the root location where binaries are installed
-	Configuration Files Path - `<config-path>` - refers to the location where configuration files, templates and other required files are saved
-	Source Path - `<src-path>` - refers to the location where project solution file (`<project-name>.sln`) is stored
-	Document Path - `<doc-path>` - refers to the root location where generated documents are to be placed
-	Documentation Entry Point - `<doc-entry-point>` - The HTML file that users will open to browse the generated documentation.

## Technology Stack
### 1. Get Binaries
>	TODO: Pointing to direct files is not good practice. update links to site download roots or `latest` points

-	http://ftp.stack.nl/pub/users/dimitri/doxygen-1.8.12-setup.exe
-	http://www.graphviz.org/pub/graphviz/stable/windows/graphviz-2.38.zip
-	http://sourceforge.net/projects/dia-installer/files/dia/0.97.2/dia_0.97.2_win32.zip/download
-	http://sourceforge.net/projects/plantuml/files/plantuml.jar/download
-	http://adoxa.altervista.org/global/dl.php?f=win32
-	https://github.com/mathjax/MathJax/archive/master.zip
-	http://www.mcternan.me.uk/mscgen/software/mscgen-w32-0.20.zip

### 2. Build stack
#### Install Doxygen, including GUI
1. 	Run doxygen-1.8.12-setup.exe
- 	Select `<install-path>` in the installation path, keep other parameters to defaults

#### Setup graphviz
1. 	Create folder `<install-path>\graphviz`
-	Extract contents of `<download-path>\graphviz-2.38.zip\release\` to folder created above

#### Setup dia
1. 	Create folder `<install-path>\dia_win32`
-	Extract contents of `<download-path>\dia_0.97.2_win32.zip\` to folder created above

#### Setup PlantUML
1. 	Copy `<download-path>\plantuml.jar` to folder `<install-path>\plantuml.jar`

#### Setup GNU Global
1. 	Create folder `<install-path>\gnu_global`
-	Extract contents of `<download-path>\glo653wb.zip\` to folder created above

#### Setup MathJax
1. 	Create folder `<install-path>\MathJax`
-	Extract contents of `<download-path>\MathJax-master.zip\MathJax-master\unpacked\` to folder created above

#### Setup MSCGEN
1. 	Create folder `<install-path>\mscgen`
-	Extract contents of `<download-path>\D:\Install-Packs\DOxygen\mscgen-w32-0.20.zip\mscgen-0.20\bin\` to folder created above

#### Configuration and support files
1.	Create folder `<config-path>`, if not already present
-	Copy all files from this folder to folder created above
	-	zPRJx-Docs-GenOpts.dat
	-	zPRJx-Docs.htm
	-	customdoxygen.css
	-	footer.html
	-	header.html
	-	DoxygenLayout.xml  

> Note: do NOT copy from rendered content, copy from `Raw` source

## Prepare
1.	Rename file `<config-path>\xPRJx-Docs-GenOpts.dat` replacing `xPRJx` with your project name or code
-	Copy file `<config-path>\zPRJx-Docs.htm` to `<doc-path>\zPRJx-Docs.htm`
-	Prepare `<doc-entry-point>`
	-	Edit file `<doc-path>\zPRJx-Docs.htm` (in notepad or any editor of your choice)
	-	Replace all instances of `xPRJx` in the file with your project code or name
	-	Save file as `<doc-path>\zPRJx-Docs.htm` replacing `xPRJx` with your project code or name

	>	Remember the renamed file name. This will later be referred to as `<doc-entry-point>`  
	>	Users will use this file as the entry point  
	>	This file is necessary as `index.htm` will be difficult to locate amongst all the generated files.  

## Configure
1.	Run `<install-path>\doxywizard.exe` to start the wizard
-	Using menu `File > Open >` select renamed file `<config-path>\xPRJx-Docs-GenOpts.dat`
-	Select TAB <u>`Wizard`</u> and select node `Project` (should be selected by default)
	-	Edit Project details as appropriate
	-	Set `Source Code Directory:` to `<src-path>`
	-	Set `Destination directory:` to `<doc-path>`
-	Select TAB <u>`Expert`</u>
-	Select node `Project`
	-	Change parameter `STRIP_FROM_PATH`, add value `<src-path>`
	-	Select node `Input`
	-	Change parameter `INPUT`, add value `<src-path>`
	-	Change parameter `HTML_HEADER`, set to value `<config-path>\header.html`
	-	Change parameter `HTML_FOOTER`, set to value `<config-path>\footer.html`
-	Select node `Dot`
	-	Change parameter `DOT_PATH`, set to value `<install-path>\graphviz`

## Generate Documentation
1.	Select TAB <u>`Run`</u>
-	Click on button `Run doxygen` to start generating documentation
-	Observe runtime messages to follow progress, and in case of any errors, review the settings to ensure all parameters are properly set

## Verify and Release
1.	Open `<doc-path>\<doc-entry-point>` in browser of your choice and inspect generated content to confirm the documentation is generated correctly
-	Zip contents of `<doc-path>` and send the zipped file

## Notes
[Comparison of documentation generators]  (https://en.wikipedia.org/wiki/Comparison_of_documentation_generators)

/
/
>	If this documentation was useful, you know what to do.
