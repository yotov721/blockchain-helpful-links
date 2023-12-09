1. Install [pandoc](https://pandoc.org/installing.html)

Download pandoc deb file https://github.com/jgm/pandoc/releases/tag/3.1.9 and install it via:

```bash
sudo dpkg -i /mnt/d/pandoc-3.1.9-1-amd64.deb
```

Create `~/.pandoc` directory if it doesn't exist. Add `templates` directory inside it
```bash
mkdir ~/.pandoc
```

Add .latex templates to .pandoc/templates/
```bash
cp /mnt/d/eisvogel.latex /home/<user>/.pandoc/templates/
```

2. Install [LaTeX](https://www.tug.org/texlive/quickinstall.html)
```bash
mkdir /tmpTex
wget https://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
cd tmpTex
zcat < install-tl-unx.tar.gz | tar xf -
cd install-tl-*
sudo perl ./install-tl --no-interaction # This can take up to 5 hours
```
Add to PATH:
```bash
echo 'export PATH=/usr/local/texlive/2023/bin/x86_64-linux:$PATH' >> ~/.bashrc
```

3. Create the PDF
```bash
pandoc audit-data/findings.md -o report.pdf --from markdown --template=eisvogel --listings
```