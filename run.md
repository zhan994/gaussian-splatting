# Quick Run

## 1 conda env

```bash
# alias pip3_install_pkg='pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple'
conda create -n gs python=3.10
conda activate gs
pip3_install_pkg torch-2.1.2+cu118-cp310-cp310-linux_x86_64.whl torchvision-0.16.2+cu118-cp310-cp310-linux_x86_64.whl torchaudio-2.1.2+cu118-cp310-cp310-linux_x86_64.whl
conda install plyfile tqdm 
pip3_install_pkg opencv-python joblib
pip3_install_pkg numpy==1.26.4
```

## 2 run

```bash
git clone git@github.com:zhan994/gaussian-splatting.git
cd gaussian-splatting
git checkout dev
git submodule update --init --recursive

pip3 install --no-build-isolation submodules/diff-gaussian-rasterization/
pip3 install --no-build-isolation submodules/simple-knn/
pip3 install --no-build-isolation submodules/fused-ssim/

python3 train.py -s data/tandt_db/tandt/train/ -m output/train/ --eval
```

# render

```bash
sudo apt install libglew-dev libassimp-dev libboost-all-dev libgtk-3-dev libglfw3-dev libavdevice-dev libavcodec-dev libxxf86vm-dev libembree-dev
cd SIBR_viewers
git checkout fossa_compatibility
cmake -Bbuild . -DCMAKE_BUILD_TYPE=Release
cmake --build build -j24 --target install
./SIBR_viewers/install/bin/SIBR_gaussianViewer_app -m output/train/
```