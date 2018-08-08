.PHONY: pdf inject-git-version verify-git-clean clean

COMMIT_SHA := $(shell git rev-parse --short=8 HEAD)

inject-git-version:
	sed -i.bak 's/\({git:\)[[:alnum:]]*\(}\)/\1${COMMIT_SHA}\2/' cv-anoff.tex

verify-git-clean:
	git diff-index --quiet HEAD

pdf:
	docker run -v ${CURDIR}:/doc/ -t -i thomasweise/texlive lualatex.sh cv-anoff.tex

clean:
	mv cv-anoff.tex.bak cv-anoff.tex

build: verify-git-clean inject-git-version pdf clean
