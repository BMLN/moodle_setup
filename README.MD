# Migrating your current moodle installation to docker

- export your database
- copy your /moodle and /moodledata folders
- run:

        docker-compose up -d moodle_db

    and after a while:

        docker-compose up -d

<br>


### Make sure your external files match!

- To run, we need a database export, the /moodle files and /moodledata files. All of them should be from the same moodle instance.

<br>


### Make sure your configuration matches the image!

- your config.php should have: 


        $CFG->dbtype    = 'mysqli';
        $CFG->dblibrary = 'native';
        $CFG->dbhost    = 'moodle_db';
        $CFG->dbname    = '<YOUR_MYSQL_DATABASENAME>';
        $CFG->dbuser    = '<YOUR_MYSQL_USERNAME>';
        $CFG->dbpass    = '<YOUR_MYSQL_PASSWORD>';
        $CFG->prefix    = 'mdl_';

        $CFG->dataroot  = '/bitnami/moodledata';

        the port is set to 3310

<br>


### Make sure the containers can use their volumes!

- your folder/files should have r/w permissions for the containers