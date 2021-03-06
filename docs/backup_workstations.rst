Backup the Workstations
=======================

.. note::  This workflow will create a single USB drive with the data backed up
 from all Tails drives. If instead you'd like to create a single duplicate
 Tails drive, you should follow the official documentation
 `maintained by the Tails project <https://tails.boum.org/doc/first_steps/persistence/copy/index.en.html>`_.

Now that you have set up the *Secure Viewing Station*, the *Admin Workstation*,
and your *Journalist Workstations*, it is important you make a backup. Your USB
drive may wear out, a journalist might lose their drive, or something completely
unexpected may happen.

In all these cases, it is useful to have a backup of your data for each device.

What You Need
-------------

  #. You will need your *existing SecureDrop Tails USB sticks* (*Admin
     Workstation*, *Journalist Workstation*, and *Secure Viewing Station*).
  #. You will also need an *airgapped machine* to perform the backups. The
     *Secure Viewing Station* may be used for this task.
  #. You will also need a "primary" Tails USB, which we will use to perform
     the backups.
  #. You also need at least one USB drive to backup the data from your current
     SecureDrop Tails USB sticks.

.. warning:: An airgapped machine (such as the *Secure Viewing Station*) is
 required in order to perform these backups safely. By isolating
 the machine from all network access, you reduce the exposure of
 sensitive data to networked computers, thereby reducing the threat
 of compromise by adversaries who wish to gain access to your
 SecureDrop instance.

The airgapped machine should have 3 USB ports, so you can plug in the *primary
Tails USB* drive, the Tails drive you want to backup, and the *backup drive* at
the same time. If you don't have 3 USB ports available you can use a USB
hub which may reduce transfer speeds.

.. note:: The steps in this section should be performed for each *Secure Viewing
 Station*, *Journalist Workstation*, and *Admin Workstation* USB drive in
 your organization.

Preparing the Backup Device
---------------------------

First you must boot the *primary Tails USB* drive. Ensure you set an administrator
password set at the login screen. Then navigate to **Applications** ▸ **Utilities** ▸ **Disks**.

|Applications Utilities Disks|

Insert the USB drive you wish to use as a backup drive.

Select the drive from the list of drives in the left column.

|Select the Disk|

Click the button with the two cogs and click **Format Partition...**.

|Click Cogs|

Fill out the form as follows:

|Format Backup Drive|

* **Erase**: `Don't overwrite existing data (Quick)`
* **Type**: `Encrypted, compatible with Linux systems (LUKS + Ext4)`
* **Name**: `Backup`

.. warning:: Since this will serve as a long-term backup, **make sure to
 use a strong passphrase**.

Click **Format**.

A dialog box will appear asking you **Are you sure you want to format the
volume?** appears, click **Format**.

Once completed, you will see two partitions appear:

|Two Partitions Appear|

Now that you made the backup device, plug in the device you want to backup.
Then, browse to **Places** ▸ **Computer**:

|Browse to Places Computer|

Click on the disk on the left side column. Fill in the passphrase you set up
when you :ref:`created your Tails devices <set_up_tails>`.

|Fill in Passphrase|

You should now have both the Backup and TailsData partition to be backed up
mounted and ready to access.

|Backup and TailsData Mounted|

Open a Nautilus window with administrative privileges by first going to
**Applications** ▸ **System Tools** ▸ **Root Terminal**.

|Root Terminal|

Type ``nautilus`` at the terminal prompt and hit enter. You'll need to type in
your administrative passphrase you set at the Tails login screen.

|Start Nautilus|

.. note:: When you run ``nautilus``, you may run into an error where Nautilus
 complains that it can't create a required folder. If that happens, just
 click OK and continue normally.

 If you can't find the "Root Terminal" window, it might be because an
 administrator passphrase wasn't set when you logged in to Tails. If
 that's the case, you'll need to restart Tails and set one at the login screen.

.. warning:: Make sure you use keep the `Root Terminal` window open while
 you perform the backups. Otherwise, the `Nautilus` window will close.

Make sure you create a directory on the backup drive to store the data from the
drive you are backing up:

|Make Folders for All Drives|

Copy over everything in the TailsData partition to the relevant folder on the
Backup drive. You can simply drag to select all the files and then copy and
paste them to the relevant folder on the Backup drive.

In particular, ensure ``gnupg`` and ``Persistent`` have been successfully
copied over. These files are critical for decrypting submissions.

Once complete, unmount the TailsData partition.

Repeat these steps for every device, making a new folder on the backup device
for each device you backup.

Finally, once you have completed the steps described in this section for each
USB drive, unmount the Backup partition and store the drive somewhere safely.

.. |Browse to Places Computer| image:: images/upgrade_to_tails_3x/browse_to_places_computer.png
.. |Click Cogs| image:: images/upgrade_to_tails_3x/click_the_button_with_cogs.png
.. |Fill in Passphrase| image:: images/upgrade_to_tails_3x/fill_in_passphrase.png
.. |Format Backup Drive| image:: images/upgrade_to_tails_3x/fill_out_as_follows.png
.. |Start Nautilus| image:: images/screenshots/root_terminal_nautilus_cli.png
.. |Make Folders for All Drives| image:: images/upgrade_to_tails_3x/make_folders_for_all_drives.png
.. |Backup and TailsData Mounted| image:: images/upgrade_to_tails_3x/backup_and_tailsdata_mounted.png
.. |Applications Utilities Disks| image:: images/upgrade_to_tails_3x/navigate_to_applications.png
.. |Root Terminal| image:: images/screenshots/root_terminal.png
.. |Select the Disk| image:: images/upgrade_to_tails_3x/select_the_disk.png
.. |Two Partitions Appear| image:: images/upgrade_to_tails_3x/two_partitions_appear.png
