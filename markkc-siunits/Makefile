.PHONY: venv test build publish

export PATH := $(CURDIR)/.venv/bin:$(PATH)

venv:
	if ! test -d .venv; then \
		python -m venv .venv; \
	fi

test: venv
	python -m pip install .[test]
	python -m pytest

build: venv test
	rm -rf dist/ build/
	python -m pip install build
	python -m build

publish: venv build
	python -m pip install twine
	python -m twine upload --repository pypi dist/*
