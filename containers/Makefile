all: hydro_precise

# change detection wasn't working properly, so falling back on phony targets for now
.PHONY: hydro_precise

hydro_precise: hydro_precise/Dockerfile
	docker build -t hydro_precise hydro_precise
