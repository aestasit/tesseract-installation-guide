# Install tesseract on Ubuntu server 12.04 LTS

    sudo apt-get update

## install compiler, etc

    sudo apt-get install build-essential
    sudo apt-get automake
    sudo apt-get install checkinstall
    sudo apt-get install subversion

## install dependencies

    sudo apt-get install autoconf automake libtool
    sudo apt-get install libpng12-dev
    sudo apt-get install libjpeg62-dev
    sudo apt-get install libtiff4-dev
    sudo apt-get install zlib1g-dev 
    sudo apt-get install libtool

## build leptonica
    
    mkdir leptonica
    cd leptonica
    wget http://www.leptonica.com/source/leptonlib-1.69.tar.gz
    tar -zxvf leptonlib-1.69.tar.gz
    cd leptonlib-1.69
    ./configure
    sudo make clean
    sudo make install -j
    sudo install
    

## build tesseract

    svn checkout http://tesseract-ocr.googlecode.com/svn/trunk/ tesseract-ocr-read-only
    cd tesseract-ocr-read-only
    ./autogen.sh --prefix=/usr
    ./configure --prefix=/usr --disable-shared
    sudo make clean 
    sudo make -j 4 
    sudo make install

## install english language pack

    wget https://tesseract-ocr.googlecode.com/files/tesseract-ocr-3.02.eng.tar.gz
    tar xf tesseract-ocr-3.02.eng.tar.gz
    sudo mkdir /usr/local/share/tessdata
    sudo cp tesseract-ocr/tessdata/*.* /usr/local/share/tessdata/
    export TESSDATA_PREFIX=/usr/local/share
