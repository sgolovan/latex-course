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

structure-title.pdf: structure-title.tex structure-wrapper.tex
	lualatex --jobname=structure-title '\input{structure-wrapper} \input{structure-title}'

structure-sections.pdf: structure-sections.tex structure-wrapper.tex
	lualatex --jobname=structure-sections '\input{structure-wrapper} \input{structure-sections}'

structure-crossref.pdf: structure-crossref.tex structure-wrapper.tex
	lualatex --jobname=structure-crossref '\input{structure-wrapper} \input{structure-crossref}'
	lualatex --jobname=structure-crossref '\input{structure-wrapper} \input{structure-crossref}'

structure-exercise-solution.pdf: structure-exercise-solution.tex
	lualatex structure-exercise-solution
	lualatex structure-exercise-solution
	lualatex structure-exercise-solution

media-graphics.pdf: media-graphics.tex structure-wrapper.tex
	lualatex --jobname=media-graphics '\input{structure-wrapper} \input{media-graphics}'
	lualatex --jobname=media-graphics '\input{structure-wrapper} \input{media-graphics}'

bib-example.pdf: bib-example.tex bib-example.bib
	lualatex --jobname=bib-example '\input{structure-wrapper} \input{bib-example}'
	biber bib-example
	lualatex --jobname=bib-example '\input{structure-wrapper} \input{bib-example}'
	lualatex --jobname=bib-example '\input{structure-wrapper} \input{bib-example}'

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
	lualatex --jobname=recap-structure '\input{structure-wrapper} \input{recap-structure}'

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
