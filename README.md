# Download repos
rm -rf layers
git clone --depth=1 --branch=kirkstone git://git.yoctoproject.org/git/poky layers/poky
# git clone --depth=1 --branch=kirkstone git://git.openembedded.org/meta-openembedded layers/meta-openembedded
git clone --depth=1 --branch=kirkstone https://github.com/stefanofiorentino/meta-uvw.git layers/meta-uvw
rm -rf build/conf
source layers/poky/oe-init-build-env
bitbake-layers add-layer ../layers/meta-uvw
bitbake uvw-example
echo "CORE_IMAGE_EXTRA_INSTALL:append = \"uvw-example\"" >> conf/local.conf
bitbake core-image-minimal
