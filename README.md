# Baikal Server Modifications (Version 0.45)

No guarantee. All changes at your own risk.

1. Modification Baikal Server Core for sending invitations
Location of the file

> baikal/Core/Frameworks/Baikal/Core/Server.php

Activation the schedule plugin by adding following lines:

    $this->server->addPlugin(new \Sabre\CalDAV\Schedule\Plugin());
    $this->server->addPlugin(new \Sabre\CalDAV\Schedule\IMipPlugin('no-reply@example.com'));

In the `if ($this->enableCalDAV)` section. Change `no-reply@example.com`.

2. Modification Sabre/Dav IMipPlugin for sending invitation with real email address
Location of the file

> baikal/vendor/sabre/dav/lib/CalDAV/Schedule/IMipPlugin.php 

Change `'From: ' . $this->senderEmail,` line in `$headers = [` section:

    'From: ' . $sender,
