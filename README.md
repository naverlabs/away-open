# AWAY Opensource 

# How to build

0. Setup build environment
   - please refer to https://source.android.com/source/initializing for the build environment
   - setup repo
     ```
     mkdir ~/bin
     PATH=~/bin:$PATH
     curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
     chmod a+x ~/bin/rep
     ```
  
1. Get Android open source from Nexell and AWAY patches
   - android version: 5.1.1  
   ```
   git clone https://github.com/naverlabs/away-open
   cd away-open
   repo init --depth=1 -u git://git.nexell.co.kr/nexell/android/lollipop/manifest -b lollipop-5.1.1_r6-avn-release_3rd
   repo sync -c
   ```

2. Apply the patches
   ```
   tar xzvf v39/s5p6818_navi.tar.gz -C device/nexell
   patch -p1 < v39/kernel.diff
   patch -p1 < v39/build.diff
   patch -p1 < v39/u-boot.diff
   patch -p1 < v39/external_sepolicy.diff
   patch -p1 < v39/external_bluetooth.diff
   patch -p1 < v39/vender_siliconcube_avrdude.diff
   patch -p1 < v39/NOTICE.diff
   ```

3. Build
   ```
   ./device/nexell/s5p6818_navi/build.sh
   make update-api
   ./device/nexell/s5p6818_navi/build.sh
   ```

# License
Please see NOTICE.html for the full open source license
