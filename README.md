# Magento-Integration

# Installation
The installation steps assume that you already have a functioning Odoo server.

If you are a developer, you may want to install the Connector using our buildout configuration, head over Connector with batteries included (buildout).

For the manual installation, just stay there.

# Requirements on both servers
The ntp package should be install on the servers hosting Magento and Odoo to ensure a correct synchronization between them

Important

Keep the git branches entire. Do not copy-paste the modules in another directory.

Add the branches in the addons path, either using the server command line or adding them in the Odoo server configuration file.

Example using the command line argument:

$ /path/to/openerp-server --addons-path /path/to/connector,/path/to/connector-ecommerce,/path/to/connector-magento,/path/to/e-commerce,/path/to/product-attribute,/path/to/sale-workflow

You also need to install the magento Python package. So install it with either pip or either easy_install:

$ pip install magento
$ easy_install magento

Note that you may need to use the root rights on your system.

In Odoo, update the modules list using Settings > Modules > Update Modules List.

Go to the menu Settings > Modules > Installed Modules, remove the Installed filter and search for Magento Connector, then click on Install.

Magento
For the time being, the Magento extension originally built by OpenLabs is still used by the connector. But the version published on Magento Connect is outdated.

Download the following Bazaar branch and install it in Magento:

$ bzr branch lp:magentoerpconnect/magento-module-oerp6.x-stable magento-module
In order to install it:

Move the Openlabs folder in the magento_root/app/code/community.
Move the file app/etc/modules/Openlabs_OpenERPConnector.xml in magento_root/app/etc/modules.
Flush the Magento cache from the admin panel or by removing everything in magento_root/var/cache
Important

This notice does not apply if you use a version of Magento above 1.7. Please check if you have installed Magento 1.7 on PHP with a 5.4.x version. Magento 1.7 is not compatible with this version and would prevent the API to behave normally. In that case, you must retrograde to PHP 5.3.x or apply the patch provided by Magento (see http://magento.com/resources/system-requirements)

Configuring the Magento web-services
In the Magento admin panel, go to System > Web-Services > SOAP/XML-RPC - Roles.
Create a new role named openerp with access to All resources.
In System > Web-Services > SOAP/XML-RPC - Users, create a new user named as you want, for instance openerp_connect, and an API key. In User Role, choose the openerp role.
