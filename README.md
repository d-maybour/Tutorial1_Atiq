# Tutorial

Tutorial provides instruction to create a new code project.

## Prerequisites: install miniconda and git

### Linux
```sh
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x Miniconda-latest-Linux-x86_64.sh
./Miniconda-latest-Linux-x86_64.sh
sudo apt install git
```

### Windows

- https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe
- https://git-scm.com/download/win

### macOS

```sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew cask install miniconda
brew cask install git
```

## 1. Create a Conda environment
```sh
conda create --name tutorial python=3.8
```

## 2. Activate the Conda environment
```sh
conda activate tutorial
```

## 3. Create a new Github repository

Visit https://github.com/new, and create a repository with the following options:
- Owner: neuromorphicsystems
- Name: whatever you want
- Private
- Untick "Initialize this repository with a README"
- Add .gitignore: None
- Add a license: None

## 4. Clone the repository
Go to your projects directory and run:
```sh
git clone https://github.com/neuromorphicsystems/whatever-you-want.git
```
Open the *whatever-you-want* directory created by *clone* command.

## 5. Create a *README*

Create a *README.md* file. It should contain a brief description of your project (see https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet for a quick syntax reference). For example:
```md
# Chaos Butterfly

Chaos Butterfly creates a web server to generates pixel butterflies!
```

## 6. Commit your README with Git

A commit contains a set of changes to one or several files. To create and share a commit, you need to:

1. add the modified files to the *tracked* files (the ones that will be part of the commit):
```sh
git add README.md
```

2. create the commit:
```sh
git commit -m "Initial commit"
```

3. push the commit to the Github server:
```sh
git push
```

## 7. List your project requirements

Create a *requirements.txt* file with the following content:
```
bottle==0.12.17
```
You can then install the dependencies with: `pip install -r requirements.txt`.

Explain to your future users how to install the dependencies in *README.md*:
```md
# Chaos Butterfly

Chaos Butterfly creates a web server to generates pixel butterflies!

## Install

Run `pip install -r requirements.txt`.
```

Commit both files:
```sh
git add README.md requirements.txt
git commit -m "List the external dependencies"
git push
```

## 8. Create the server skeleton
1. Copy the *render.py* and *server.py* files from this repository to yours.
2. Commit both files.
3. Start the server:
```sh
python server.py
```
4. Visit http://localhost:8080/100/100. You should see a black square.

## 9. Write the butterfly server

Write the server implementation in *server.py*. You don't need to modify *render.py* (but you can if you want to).

A request to the route `http://localhost:8080/<width:int>/<height:int>` must return a `<width>` by `<height>` grayscale image with random pixel values constrained by two symmetry axis (horizontal and vertical). If one of the parameters is not a multiple of two, it must be rounded up. Null or negative parameters must be interpreted as the value 2.

You may use external libraries, as long as you add them to *requirements.txt*.

For example, http://localhost:8080/200/200 must return an image such as:

![example](example.png)

Feel free to add other features to your code. Don't forget to commit all your changes.

## 10. Share your code

Give your repository address to someone else. This new developer should be able to install and use your server without your help.
