# pdftoref

`pdftoref` extracts DOIs from .pdf files, and outputs references (BibTex and APA formats).

With the `-g` option, it saves references and organizes/classes your papers in `$HOME/papers` (with this name format : "(author)(year).pdf").

# What it does

What `pdftoref` does first is
- **(1)** searches for a DOI in the pdf
- **(2)** looks in Crossref for references thanks to DOI
- **(3)** checks if the title found on Crossref matches the paper's (if yes : outputs references ; if not sure : asks for a confirmation ; if no : asks to enter the title manually).

If DOI can't be found :
- **(1)** uses `pdftitle` (see below) to extract the title
- **(2)** asks if found title matches the paper's (if yes : outputs references ; if not sure : asks for confirmation ; if no : asks to enter the title manually).


When using the `-g` option, it automatically checks if the paper is already in `$HOME/papers`. If an author has published more than one paper during the same year, papers will not be confused (if they're really different papers, else `pdftoref` will pass), and the last paper added to the `$HOME/papers` folder will be renamed this way : (author)(year)a.pdf.

Will soon add an option to deactivate the "ask for title manually" sequence.

## Getting Started

### Prerequisites

`pdftoref` should work out of the box. However, you may have to install some dependencies for optimal use :

* pdftitle (necessites python) : see https://pypi.org/project/pdftitle/
* zathura (pdf reader). When `pdftoref` can't find the DOI, it looks for the title. If it can't extract it, you are asked if you want to open the file with zathura (did not manage to find a way to open the default pdf reader on the machine) <!--If it can't find the title, it prints a preview (20 first lines) in the terminal, so you can copy and paste it. -->

#### For Ubuntu, Debian

```
sudo apt install python pip
pip install pdftitle
sudo apt install zathura
```

#### For Arch

```
sudo pacman -S python pip
pip install pdftitle
sudo pacman -S zathura
```

# Installing pdftoref

To try `pdftoref`, you can clone this repository. For instance :

```
cd ~
git clone https://github.com/dougy147/pdftoref
```

or just download `pdftoref` and put it in your scripts folder.

Then, open your terminal, go to the folder you just cloned :

```
cd ~/pdftoref
```

And launch it using a pdf as first argument :

```
pdftoref ~/downloads/paper.pdf #supposing your pdf paper is in the downloads folder
```

If it doesn't work, try to add `sh` at the beginning of the line (e.g. `sh pdftoref ~/downloads/paper.pdf`).

# Examples

Here's the result of `pdftoref` with a recent paper.

![](images/example1.png)

If you want to extract references from a bunch of pdfs, go to the folder which contains your pdfs and type :

```
for x in *pdf ; do pdftoref "$x" ; done
```

and `pdftoref` will iteratively check for references of all pdfs in the folder. Don't forget the `-g` option to get your papers references' saved in `$HOME/papers`.

# More info

Tested passively on a 155 pdf database (containing papers from year 1892 to 2019), `pdftoref` is 85% accurate in finding references. 11 papers (7%) have been mistaken with other papers (may be corrected by adding name of the author when searching with the title). 13 papers (8%) have been found on Google Scholar only, but at the time, I have not been able to automatically extract references from a Google Scholar search (work in progress). 131 papers (85%) have been correctly identified.
