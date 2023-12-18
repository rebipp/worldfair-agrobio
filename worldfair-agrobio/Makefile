all: build

build:
	jupyter-book build -n .

serve: build
	python tools/serve.py

clean:
	rm -rf _build/
