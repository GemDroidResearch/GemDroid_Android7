# GemDroid
This repository contains GemDroid-related gem5 modifications.

## Build
	git clone https://github.com/GemDroidResearch/GemDroid_gem5_Android7.git
	cd GemDroid_Android7
	git clone https://gem5.googlesource.com/public/gem5
	cd gem5/
	git checkout 0be64ff
	rm -rf src/
	cp -r ../gemdroid.src ./src
	cp -r ../gemdroid.needed/gemdroid.dramsim2/* ./ext/dramsim2/
	mkdir traces
	cp your_trace.trace traces/
	cp ../gemdroid.needed/*.txt ./
	scons build/ARM/gem5.debug 
	
## Run
	build/ARM/gem5.debug -d results/test configs/example/se.py -n 1 --cpu-type=timing --caches --l2cache --num-dirs=1 --gemdroid --cpu_trace1 traces/your_trace.trace --num_cpu_traces=1 --device_config=ini/your_device_config.ini --system_config=your_system_config.ini -c tests/test-progs/hello/bin/arm/linux/hello


