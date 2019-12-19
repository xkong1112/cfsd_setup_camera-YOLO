# cfsd_setup_camera-YOLO
Commend used for set-up the camera zed and YOLO, Nviidia docker need to be installed first for GPU speed up.
Seting up the camera ZED
```
nvidia-docker run -ti --rm --privileged --init --ipc=host --net=host -e DISPLAY=$DISPLAY -v /tmp:/tmp chalmersrevere/opendlv-device-camera-zed-amd64:v0.0.2 opendlv-device-camera-zed --profile=1280x720@60 --verbose

```
Running YOLO
```
nvidia-docker run -ti --rm --privileged --init --ipc=host --net=host -e DISPLAY=$DISPLAY -v /tmp:/tmp -v ${PWD}/custom.cfg:/opt/yolo.cfg -v ${PWD}/custom.weights:/opt/yolo.weights chalmersrevere/opendlv-perception-detect-yolo-amd64:v0.0.1 opendlv-perception-detect-yolo --cid=111 --cfg-file=/opt/yolo.cfg --weight-file=/opt/yolo.weights --name=video0 --width=1280 --height=720 --verbose

```
