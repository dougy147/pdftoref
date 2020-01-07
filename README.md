# pdftoref

`pdftoref` extracts DOIs from .pdf files, outputs and saves references (BibTex and APA formats), and organizes/classes your articles in `$HOME/articles`.

## Getting Started

### Prerequisites

`pdftoref` should work out of the box. However, you may have to install some dependencies optimal use :

* pdftitle (necessites python) : see https://pypi.org/project/pdftitle/
* facultative : zathura (pdf reader). When `pdftoref` can't find the DOI, it looks for the title. If it can't extract it, you are proposed to open the file with zathura (did not manage to find a way to open the default pdf reader on the machine) <!--If it can't find the title, it prints a preview (20 first lines) in the terminal, so you can copy and paste it. -->

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

### Installing

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
pdftoref ~/downloads/article.pdf #supposing your pdf article is in the downloads folder
```

If it doesn't work, try to add `sh` at the beginning of the line (e.g. `sh pdftoref ~/downloads/article.pdf`).

# Examples

Here's the result on `pdftoref` with a recent article.

![](images/example1.png)

If you want to extract references from a bunch of pdfs, go to the folder which contains your pdfs and type :

```
for x in *pdf ; do pdftoref "$x" ; done
```
and `pdftoref` will iteratively check for references of all pdfs in the folder.

# More info

Tested passively with a 155 pdf database (containing articles from year 1892 to 2019), `pdftoref` is 85% accurate in finding references. It has been tested on a 155 pdf database (containing articles from year 1892 to 2019). 11 of them (7%) were mistaken with other articles (may be corrected by adding name of the author when searching with the title). 13 of them (8%) have been found on Google Scholar only, but at the time, I have not been able to automatically extract references from a Google Scholar search in a proper manner (work in progress).
