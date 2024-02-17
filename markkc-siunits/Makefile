.PHONY: venv test build publish

export PATH := $(CURDIR)/.venv/bin:$(PATH)

venv:
	if ! test -d .venv; then \
		python -m venv .venv; \
	fi

test: venv
	pip install .[test]
	pytest

build: venv test
	rm -rf dist/ build/
	pip install build
	python -m build

publish: venv build
	pip install twine
	python -m twine upload --repository pypi dist/*
