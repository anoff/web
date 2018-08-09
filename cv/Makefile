.PHONY: pdf inject-git-version verify-git-clean clean commit

COMMIT_SHA := $(shell git rev-parse --short=8 HEAD)
FILE_TEX := ./cv-anoff.tex # latex filename
FILE_PDF := ./cv-anoff.pdf # desired pdf filename
FILE_OUT = $(shell echo ${FILE_TEX} | sed -e 's/\.tex/\.pdf/') # the (intermediate) file outputted by tex

inject-git-version:
	sed -i.bak 's/\({git:\)[[:alnum:]]*\(}\)/\1${COMMIT_SHA}\2/' ${FILE_TEX}

verify-git-clean:
	git diff-index --quiet HEAD

pdf:
	docker run -v ${CURDIR}:/doc/ -t -i thomasweise/texlive lualatex.sh ${FILE_TEX}

clean:
	mv ${FILE_OUT} ${FILE_PDF}
	mv ${FILE_TEX}.bak ${FILE_TEX}

commit:
	git commit -am ":construction_worker: build: CV update"

build: verify-git-clean inject-git-version pdf clean commit
