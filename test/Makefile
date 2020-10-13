test:
	echo "Making test inside test directory"
	docker run --rm -v $(HOST_WD):/tmp/build -v /var/run/docker.sock:/var/run/docker.sock -it $(GBOX):$(VER) python ./beta_to_m.py
