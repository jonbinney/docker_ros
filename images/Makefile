all: savibot ros_hydro_precise

# change detection wasn't working properly, so falling back on phony targets for now
.PHONY: ros_hydro_precise

ros_hydro_precise: hydro_precise/Dockerfile
	docker build -t ros_hydro_precise ros_hydro_precise
