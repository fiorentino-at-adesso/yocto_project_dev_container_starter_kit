# Download repos
rm -rf layers
git clone --depth=1 --branch=kirkstone git://git.yoctoproject.org/git/poky layers/poky
git clone --depth=1 --branch=kirkstone git://git.openembedded.org/meta-openembedded layers/meta-openembedded
rm -rf build/conf
source layers/poky/oe-init-build-env
bitbake core-image-minimal
