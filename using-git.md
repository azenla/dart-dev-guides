# Using Git

Since Dart uses Subversion, in order to develop Dart with Git, you will have to use the git-svn tool.

## Depot Tools

If you have already installed depot tools, please skip this section and move on to `Cloning the Code`

To Install Depot Tools, run the following commands outside of where you want your Dart Code:
```bash
# Clones the Depot Tools
git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
# Add Depot Tools to your current Shell's PATH Variable (for just this session)
export PATH=$PATH:`pwd`/depot_tools
# Adds the Depot Tools to your path via your .bashrc file (so you don't have to update PATH every time)
echo "export PATH=$PATH:`pwd`/depot_tools" >> ~/.bashrc
```

## Cloning the Code

Inside the directory you want the Dart Code to live, execute the following commands:
```bash
# Initializes the .gclient configuration
gclient config https://dart.googlecode.com/svn/branches/bleeding_edge/deps/all.deps
# Clones the Subversion repository using git-svn 
git svn clone -rHEAD https://dart.googlecode.com/svn/branches/bleeding_edge/dart dart
# Fetches Other Repositories
gclient sync -n
# Runs gclient hooks
gclient runhooks
```

## Contributing

Dart uses the standard Google Open Source workflow:

- Create Branch
- Write Code
- Commit
- Upload Patch for Review

Creating a Feature Branch:
```bash
# Creates a Feature Branch
git checkout -b <feature-branch-name>
```

After you have written some code, commit it:
```bash
# Commits your Code
git commit
```

### Code Style

Dart has specific code guidelines that are generally from the [Google Style Guide](https://code.google.com/p/google-styleguide/).

[C++](http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml) | [Java](http://google-styleguide.googlecode.com/svn/trunk/javaguide.html) | [Python](http://google-styleguide.googlecode.com/svn/trunk/pyguide.html) | [JavaScript](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml) | [Shell Script](http://google-styleguide.googlecode.com/svn/trunk/shell.xml)

And for Dart Code, follow the [Dart Style Guide](https://www.dartlang.org/articles/style-guide/).

### Submitting for Code Review

To Configure Code Review, run the following command:
```bash
# Sets Up Code Review
# Rietveld Server: https://codereview.chromium.org/
# Leave all other fields blank
git cl config
```

Then, upload your patch:
```bash
# Uploads Your Patch
git cl upload
```

When your patch has been submitted for review, attach the review to [a new Dart Issue](http://dartbug.com/new).

If you have commit access, run the following command after the review is done and the patch is ready to directly commit the patch:
```bash
# Directly Commits the Patch
git cl dcommit
```
