all: part1.pdf part2.pdf part3.pdf

#
# Part 1
#
part1.pdf: part1.tex preamble.tex
	lualatex -shell-escape part1
	lualatex -shell-escape part1

#
# Part 2
#
part2.pdf: part2.tex preamble.tex structure-title.pdf structure-sections.pdf structure-crossref.pdf media-graphics.pdf bib-example.pdf structure-exercise-solution.pdf
	lualatex -shell-escape part2
	lualatex -shell-escape part2

structure-title.pdf: structure-title.tex
	lualatex structure-title

structure-sections.pdf: structure-sections.tex
	lualatex structure-sections

structure-crossref.pdf: structure-crossref.tex
	lualatex structure-crossref
	lualatex structure-crossref

structure-exercise-solution.pdf: structure-exercise-solution.tex
	lualatex structure-exercise-solution
	lualatex structure-exercise-solution
	lualatex structure-exercise-solution

media-graphics.pdf: media-graphics.tex
	lualatex media-graphics
	lualatex media-graphics

bib-example.pdf: bib-example.tex bib-example.bib
	lualatex bib-example
	bibtex bib-example
	lualatex bib-example
	lualatex bib-example

#
# Part 3
#
part3.pdf: part3.tex preamble.tex recap-structure.pdf recap-exercise.pdf recap-exercise-solution.pdf beamer-minimal.pdf beamer-theme.pdf beamer-exercise.pdf beamer-exercise-solution.pdf
	lualatex -shell-escape part3
	lualatex -shell-escape part3

recap-exercise.pdf: recap-exercise.tex
	lualatex recap-exercise

recap-exercise-solution.pdf: recap-exercise-solution.tex
	lualatex recap-exercise-solution

recap-structure.pdf: recap-structure.tex
	lualatex recap-structure

beamer-minimal.pdf: beamer-minimal.tex
	lualatex beamer-minimal

beamer-theme.pdf: beamer-theme.tex
	lualatex beamer-theme

beamer-exercise.pdf: beamer-exercise.tex
	lualatex beamer-exercise

beamer-exercise-solution.pdf: beamer-exercise-solution.tex
	lualatex beamer-exercise-solution
	lualatex beamer-exercise-solution

latex-course.tgz: part1.pdf part2.pdf part3.pdf basics-exercise-1-solution.tex basics-exercise-1.tex basics-exercise-2-solution.tex basics-exercise-2.tex basics.tex bib-example.tex preamble.tex structure-exercise-solution.tex structure-exercise-solution.pdf structure-exercise.tex big_chick.png bib-exercise.bib recap-exercise.tex recap-exercise-solution.pdf beamer-minimal.tex beamer-exercise.tex beamer-exercise-solution.pdf gettysburg_graph.png
	tar czf latex-course.tgz $^

clean:
	rm -f *.log *.aux *.out *.nav *.snm *.toc *.vrb *.pyg *.bbl *.blg structure-crossref.pdf structure-sections.pdf structure-title.pdf media-graphics.pdf bib-example.pdf

clobber: clean
	rm -f part1.pdf part2.pdf part3.pdf
