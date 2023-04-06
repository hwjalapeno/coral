sudo apt-get dist-upgrade
export DEMO_FILES="$HOME/demo_files"
wget -P ${DEMO_FILES}/ https://github.com/google-coral/test_data/raw/master/mobilenet_v2_1.0_224_quant_edgetpu.tflite

wget -P ${DEMO_FILES}/ https://raw.githubusercontent.com/google-coral/test_data/release-frogfish/imagenet_labels.txt

# The face detection model (does not require a labels file)
wget -P ${DEMO_FILES}/ https://github.com/google-coral/test_data/raw/master/ssd_mobilenet_v2_face_quant_postprocess_edgetpu.tflite

edgetpu_detect_server \
--source /dev/video1:YUY2:800x600:24/1  \
--model ${DEMO_FILES}/ssd_mobilenet_v2_face_quant_postprocess_edgetpu.tflite
