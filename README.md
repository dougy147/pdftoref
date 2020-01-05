# pdftoref

Pdftoref extracts DOIs from .pdf files, outputs and saves references (BibTex and APA formats), and organizes/classes your articles in `$HOME/articles`.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

Pdftoref should work out of the box. However, you may have to install some dependencies to make it work properly :

* pdftitle (necessites python) : see https://pypi.org/project/pdftitle/
* zathura (pdf reader)

```
pip install pdftitle
sudo pacman -S zathura # or sudo apt install zathura
```

### Installing

To try `pdftoref`, you can clone this repository. For instance :

```
git clone https://github.com/dougy147/pdftoref ~
```

Then, open your terminal and go to the folder you just cloned :

```
cd ~/pdftoref
```

And launch it using a pdf as first argument :

```
sh pdftoref ~/downloads/article.pdf # supposing your pdf article is in the downloads folder
```

![](images/example1.png)

