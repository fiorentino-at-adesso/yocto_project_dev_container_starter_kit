# Download repos
rm -rf layers && mkdir -p layers && cd layers
git clone --depth=1 --branch=kirkstone git://git.yoctoproject.org/git/poky
git clone --depth=1 --branch=kirkstone git://git.openembedded.org/meta-openembedded
cd -
rm -rf build/conf
source layers/poky/oe-init-build-env
bitbake core-image-minimal
