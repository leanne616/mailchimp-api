MailChimp API
=============

Super-simple, minimum abstraction MailChimp API v2 wrapper, in PHP.

I hate complex wrappers. This lets you get from the MailChimp API docs to the code as directly as possible.

Requires curl and a pulse. Abstraction is for chimps.

Installation
------------

You can install the mailchimp-api using Composer.  Just add the following to your composer.json:

    {
        "require": {
            "drewm/mailchimp-api": "*"
        }
    }

You will then need to:
* run ``composer install`` to get these dependencies added to your vendor directory
* add the autoloader to your application with this line: ``require("vendor/autoload.php")``

We're not on Packagist (yet! Remove this line and the code block below when that happens) so you'll also need to add the repo as a remote by adding a repositories block to the composer.json file:

    "repositories": [
        {
            "type" : "vcs",
            "url" : "https://github.com/drewm/mailchimp-api"
        }   
    ],


Examples
--------

List lists (lists/list method)

	<?php
	$MailChimp = new \drewm\MailChimp('abc123abc123abc123abc123abc123-us1');
	print_r($MailChimp->call('lists/list'));

Subscribe someone to a list

	<?php
	$MailChimp = new \drewm\MailChimp('abc123abc123abc123abc123abc123-us1');
	$result = $MailChimp->call('lists/subscribe', array(
					'id'                => 'b1234346',
					'email'             => array('email'=>'davy@example.com'),
					'merge_vars'        => array('FNAME'=>'Davy', 'LNAME'=>'Jones'),
					'double_optin'      => false,
					'update_existing'   => true,
					'replace_interests' => false,
					'send_welcome'      => false,
				));
	print_r($result);


*Note for contributors:* This is not Code Golf.
