Link to google doc ( https://docs.google.com/document/d/1ufXISMssgG6uR4WtB5TfNIXlbC2fZndHdGhUn8Ke7i8/edit?usp=sharing ).

Installing Odoo Enterprise
There are multiple ways to install Odoo, depending on your use case.
Online
The easiest way to use Odoo in production or to try it.
Packaged installers
Suitable for testing Odoo, and developing modules and can be used for long-term production use with additional deployment and maintenance work.
Source install
Provides greater flexibility: e.g. allow multiple running Odoo versions on the same system. Good for developing modules, and can be used as a base for production deployment.
Docker
If you usually use docker for development or deployment, an official docker base image is available.

 This document will describe the Packaged installer's method to install odoo on-premise. 
( In this guide we use ubuntu server 22.04 lts on Digital Ocean ).

Before Following the below instructions I assume you have a Linux development environment with ubuntu 22.04 lts.
Odoo Enterprise Installation on ubuntu 22.04 Using Package

Odoo provides packaged installers for Windows, deb-based distributions (Debian, Ubuntu, …), and RPM-based distributions (Fedora, CentOS, RHEL, …) for both the Community and Enterprise versions.

These packages automatically set up all dependencies (for the Community version), but may be difficult to keep up-to-date.

 Both Community and Enterprise packages can be downloaded from our download page ( you must be logged in as a paying customer or partner to download the Enterprise packages ).
Step 1 - Install  PostgreSQL. 


The default configuration for the Odoo ‘deb’ package is to use the PostgreSQL server on the same host as your Odoo instance.:

Odoo needs a PostgreSQL server to run properly.

Execute the following command in order to install the PostgreSQL server:
     $ sudo apt install postgresql -y

Step 2 - Install wkhtmltopdf (  0.12.5 ).
The version of wkhtmltopdf available in Debian/Ubuntu repositories does not support headers and footers while we generate a pdf report in odoo, so version ( 0.12.5 ) must be downloaded from the project's page and is recommended for odoo version 10 and later.

See the below screenshot from the odoo wiki

Download the package
    wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb

Install the package

  sudo dpkg -i wkhtmltox_0.12.5-1.bionic_amd64.deb

 This probably fails with missing dependencies because wkhtmltopdf version(  0.12.5 ) needs ( libssl1.1 ) but ubuntu 22.04 uses (libssl3) so you have to manually setup libssl1.1 

Fix dependencies

sudo apt install -f
Step 3 - Download and setup Odoo  Enterprise editions


Enterprise editions can be downloaded from the official download page.


Download the enterprise edition for Ubuntu.Debian. You will be asked for your subscription code. 

Enter your subscription code and download will start.

 Upload the file to your server root folder.


And Install the package using the command 

   $ dpkg -i <path_to_installation_package>


In my case its - $  dpkg -i odoo_16.0+e.latest_all.deb


  
This command will fail with missing dependencies. Take a screenshot or list down the missing packages

After that to  install the missing dependencies  run command 

  apt-get install -f 
      

If encounter any error related to a specific package. List the package and install it manually.

Run the Installation command again 
dpkg -i <path_to_installation_package>

All Done  Now Navigate to url: https://your.ip:8069

And you will see something Like -

Fill in the details  and press Create database.

 You will we navigated to the login page.

Fill in the details you entered while creating data base and login. You will be redirected to home page. 


In the above tutorial we have successfully installed odoo Enterprise  using Packaged Installers Method. 




           

 

