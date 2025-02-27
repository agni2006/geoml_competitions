# 2021 Seismic Inversion Challenge

This is the installation guide for the serverless data available through 
the GSH Geophysics on the cloud challenge. SEGY, rss and OpenVDS data is available:

s3://geophysics-on-cloud/poseidon/seismic

SEGY can be read directly using boto3 or s3fs, rss and OpenVDS+ require additional 
python libraries to access.

# RSS - Python Installation

## Windows, OSX, Ubuntu, ....  Python 3.6, 3.8, 3.9

pip install real-simple-seismic

# OpenVDS - Python Installation

[Download] https://bluware.com/downloads/download-openvds/

## Windows - Working Conda + Python 3.8

Download the Windows OpenVDS+ wheel file and unzip it. 

From the power shell (inside VsCode for example) run:
pip install .\openvds+-2.0.2\openvds-2.0.2-cp38-cp38-win_amd64.whl

This has been tested by multiple users and appears to work.

## Redhat/Centos 7 -  Untested Requires Python 3.6

## Ubuntu - Issues Conda + Python 3.8

Download the Ubuntu OpenVDS+ wheel file and untar it

tar -zxvf openvds+-2.0.2-ubuntu-20.04.tar.gz\
pip install openvds+-2.0.2/openvds-2.0.2-cp38-cp38-linux-x86_64.whl

## Issues:
import openvds\
throws some errors around missing libraries, which can be fixed by installing 
the libraries with apt or conda, for the apt examples:

sudo apt upgrade apt\
sudo apt-get install -y libgomp1\
sudo apt-get install -y libboost1.71-all-dev

or,\
conda install -c anaconda libgomp\
conda install -c conda-forge boost

The final issues comes from the version of libssl.

### Warning this may screw up your conda install

import openvds\
libssl.so.1.1: undefined symbol EVP_idea_cba, version OPENSSL_1_1_0

A work around here is to copy system libssl.a, libssl.so, libssl.1.1 into:\
~/miniconda3/lib\
Assuming conda is installed in the default location.

This seems to work, but it's unclear how stable this solution is going to be.



