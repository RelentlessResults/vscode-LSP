# Vscode-LSP
Vscode-LSP is a Language server + client for Visual Studio Code, that enables basic programmatic language features for the iAccess JSON schema.

## Start using Vscode-LSP

Vscode-LSP is published in the Visual Studio Marketplace, and can be found using the keywords "json lsp". Click the install button, and when you open a folder containing an "application.json" file somewhere in its path, the extension will become active.

## Features
Once you open a .json file in a workspace folder containing a "application.json" file, the extionsion will activate.

This will provide diagnostics for the "$ref":"URI" pattern, giving you an error if the URI you have written does not correspond to a file in the folder. 

Vscode-LSP also provides quick navigation throughout the directories of iAccess.
If a path exists, you can use Ctrl + click to open the referenced file, or right click and use "goto definition".

![](images/extension.gif)

Besides providing diagnostics for the "$ref":"URI" pattern, vscode-LSP also checks if a schema is provided for the application and validates against it. Thus it will provide diagnostics
for properties, where there are missing requiered properties, or unallowed additional proporties.

It is important to notice that the extension uses the saved file, and will thus only update upon saving a file with changes.
# Development
### Prerequisites
Only prerequisite for using the extension is Visual Studio Code

For development having node and npm installed is a requirement. This can be downloaded through nvm(Node Version Manager), which is prefered as the repository provides a .nvmrc. Nvm are available for macOS via Homebrew and Windows via Chocolatey.

After installing npm, use it to install typescript globally
```
npm install -g typescript
```

### Development

Download the source from github

```
git clone https://github.com/Johanpdrsn/vscode-LSP
```

Then install all dependencies

```
npm install
```

The repository comes with a launch configuration, so to launch the extension in a "Extension Development Host" just go to debugging in the side bar, and select "Launch Client".
This will open up a new window with the extension running in debugging mode. 
All communication between the server and the client is logged in the "Language Server" channel. This can be found under "output" and selecting  "Language Server", and toggled on and of extension manifest(package.json).

There are 3 main files to look at when developing the extension:
1. Package.json - All contributions and dependencies of the extension are listed here.
2. client/src/extension.ts - The source code for the client part of the LSP
3. server/src/server.ts - The source code for the server part of the LSP

## Running the tests

The tests in the client/src/test folder, are end-2-end test using the mocha framework. These can be executed by going to the debugger and selecting "Run Tests". Again this will open a new window, performing the tests on the json files found under "TestFixtures". 

## Deployment

Deployment to the Visual Studio Marketplace is done with the vsce tool. Integration with Jenkins is on the roadmap.

## Contributing

Bugs and feature requests can be reported in the [Gitub Issues](https://github.com/Johanpdrsn/vscode-LSP/issues).


## Versioning

We use [SemVer](http://semver.org/) for versioning.
