# $Id: Makefile,v 1.4 2004/03/30 00:13:57 jschauma Exp $

TARGET	=	slides
BIBLIO	=	slides.bib

LATEX	=	latex
BIBTEX	=	bibtex
DVIPS	=	dvips -o
PS2PDF	=	ps2pdf
PDFTOTEXT=	pdftotext

PICTURES=	pics/http-proposal-detail.eps \
		pics/datatransfer.eps \
		pics/crypto-accelerator.eps \
		pics/DSR.eps \
		pics/One-armed-outbound.eps \
		pics/One-armed-inbound.eps \
		pics/Lb101.eps \
		pics/cdn.eps \
		pics/firebug.eps \
		pics/chrome-tools.eps

.SUFFIXES: .tex .dvi .ps .pdf .txt .fig .eps .jpg .png .gif

all:	$(PICTURES) $(FIGURES) $(TARGET).dvi

show: $(PICTURES) ${TARGET}.dvi
	xdvipresent xga ${TARGET}.dvi -paper 25.8x19.3 -geometry 1024x764-0-0

slides:	$(PICTURES) #example.knuth.eps example.knuth2.eps example.knuth3.eps

.tex.dvi:
	$(LATEX) $<
	$(LATEX) $<

.fig.eps:
	fig2dev -L eps $< > $@

ps:	$(TARGET).dvi $(TARGET).ps

# PS will be upside down - add the following line after each "%%Page: "
# directive:
# 180 rotate -612 -792 translate
.dvi.ps:
	$(DVIPS) $@ $<

.jpg.eps:
	convert $< $@

.png.eps:
	convert $< $@

.gif.eps:
	convert $< $@

pdf:  ${PICTURES} $(TARGET).dvi $(TARGET).ps $(TARGET).pdf

txt: $(TARGET).dvi $(TARGET).ps $(TARGET).pdf $(TARGET).txt

html:
	latex2html $(LATEX2HTMLOPTS) $(TARGET).tex

.ps.pdf:
	$(PS2PDF) $< $@

.pdf.txt:
	$(PDFTOTEXT) $< $@

clean:
	rm -f *.out **.bbl *.blg *.log *.aux *.dvi *.ps *.pdf *.toc *.bak *.lof ${PICTURES}
	rm -fr $(TARGET)/
