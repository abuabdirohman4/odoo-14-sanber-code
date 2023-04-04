# Sanber Code Bootcamp
Odoo
----

Odoo is a suite of web based open source business apps.

The main Odoo Apps include an <a href="https://www.odoo.com/page/crm">Open Source CRM</a>,
<a href="https://www.odoo.com/page/website-builder">Website Builder</a>,
<a href="https://www.odoo.com/page/e-commerce">eCommerce</a>,
<a href="https://www.odoo.com/page/warehouse">Warehouse Management</a>,
<a href="https://www.odoo.com/page/project-management">Project Management</a>,
<a href="https://www.odoo.com/page/accounting">Billing &amp; Accounting</a>,
<a href="https://www.odoo.com/page/point-of-sale">Point of Sale</a>,
<a href="https://www.odoo.com/page/employees">Human Resources</a>,
<a href="https://www.odoo.com/page/lead-automation">Marketing</a>,
<a href="https://www.odoo.com/page/manufacturing">Manufacturing</a>,
<a href="https://www.odoo.com/#apps">...</a>

Odoo Apps can be used as stand-alone applications, but they also integrate seamlessly so you get
a full-featured <a href="https://www.odoo.com">Open Source ERP</a> when you install several Apps.

Getting started with GNBS Project Module
-------------------------

For installation please follow this Setup instructions.

To learn the software, we recommend the <a href="https://www.odoo.com/slides">Odoo eLearning</a>, or <a href="https://www.odoo.com/page/scale-up-business-game">Scale-up</a>, the <a href="https://www.odoo.com/page/scale-up-business-game">business game</a>. Developers can start with <a href="https://www.odoo.com/documentation/13.0/developer/howtos.html">the developer tutorials</a>

## Install PostgreSQL With Brew & Run it
```
brew install postgresql
brew services start postgresql
```

## Add Python Local
```
pyenv local 3.6.15
```

## Initialitation Git
```
git init
```
Create file .gitgnore
```
touch .gitignore
```
Then fill with this
```
venv
odoo
```

## Download odoo 
```
git clone https://www.github.com/odoo/odoo --depth 1 --branch 13.0 odoo
```

## Remove git from Odoo folder
```
rm -rf ./odoo/.git*
```

## Handle Error ValueError('unknown locale: %s' % localename)
Open file ~/.zprofile & source ~/.zprofile
```
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
```

## Handle Error gevent
```
brew install libpq --build-from-source

export LDFLAGS="-L/opt/homebrew/opt/openssl@1.1/lib -L/opt/homebrew/opt/libpq/lib"
export CPPFLAGS="-I/opt/homebrew/opt/openssl@1.1/include -I/opt/homebrew/opt/libpq/include"
```

## Virtual Environment
```
python -m venv venv
source venv/bin/activate
```

## Install Package
```
CFLAGS="-Wno-error=implicit-function-declaration" pip install reportlab==3.5.55
pip install wheel Cython==3.0.0a10
pip install gevent==20.9.0 --no-build-isolation
pip install -r ./odoo/requirements.txt
```

## Handle --limit-memory-hard 0
Comment at file /odoo/odoo/service/server.py in line ke-82
```
resource.setrlimit(rlimit, (config['limit_memory_hard'], hard))
```

# Create Odoo Configuration
```
touch odoo.conf
```
and then add this code at the file
```
[options]
addons_path = ./odoo/addons, extra-addons
# db_host = False
# db_port = 5432
# db_user = odoo
# db_password = False
# db_filter = live
# http_port = 8069
```

## Create Extra Addons folder
```
mkdir extra-addons
```

## Running Odoo
```
./odoo/odoo-bin -c odoo.conf
```