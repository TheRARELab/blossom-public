
# How to run the `start_asr.py` code in 3.11.2

## 1: Install build tools and depen
```
sudo apt install build-essential libasound-dev
```
## 2: Download and build `portaudio` library
```
cd ~
git clone https://github.com/PortAudio/portaudio.git
cd portaudio
./configure
make
sudo make install
```

This will create a new portaudio folder in your home directory that contains the `portaudio` library however it is not ready to use yet 

## 3: Locate the file 

In the terminal type:
```
find ~ -name "libportaudio.so.2"
```

It will return the path with something similar to this 
```
/home/blossompi3/portaudio/lib/.libs/libportaudio.so.2
```

## 4: Load the library permanently 
Run this and make sure to change the necessary details to match your path 
```
echo 'export LD_LIBRARY_PATH=/home/blossompi3/portaudio/lib/.libs:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```
This allows the library to be loaded in your `bashrc` and be recognized when imported

## 5: Load into your virtual environment

```
python -m venv testing
source testing/bin/activate
```

## 6: Install the requirements

```
pip install -r new_requirements.txt
```

## 7:Run the program
```
python3 start_asr.py
