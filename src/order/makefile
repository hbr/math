build-dir    = ../../_build/order
gh-pages-dir = ../../gh-pages


source-files = \
	ord_main.tex \
	ord_macros.tex \
	ord_poset.tex  \
	ord_lattice.tex


# Generate a pdf from scratch:
#     make pdf			1st pass collect all references
#     make bib			extract from bib database
#     make pdf			2nd pass update references


# Run pdflatex and generate the pdf file (only once)
# Run it twice to get crossreferences correct if new labels have been
# introduced.
.PHONY: pdf
pdf: mk-build-dir
	rm $(build-dir)*.tex;  \
	cp $(source-files) $(build-dir); \
	(cd $(build-dir); pdflatex ord_main.tex)


# Extract citations for the bib database. Run always, if a new citation has been
# added.
.PHONY: bib
bib: mk-build-dir
	(cd $(build-dir); bibtex cmp)


.PHONY: mk-build-dir
mk-build-dir:
	test -d "$(build-dir)" || mkdir -p $(build-dir)




# Github Pages
#======================================================================

.PHONY: gh-pages
gh-pages:
	cp $(build-dir)/cmp.pdf $(gh-pages-dir); \
	(cd $(gh-pages-dir); git commit -a --amend --no-edit; git push -f)
