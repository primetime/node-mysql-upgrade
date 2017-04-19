# MySQL Upgrade
A simple MySQL database upgrade module based on plain SQL files. For developers who don't use an ORM like Sequelize, but still want to have a `database.sync();` functionality.

```
npm install mysql-upgrade
```

## Requirements
This module only works with Node 7.6 or later (because of native support for `async/await`).

## How to use
```Javascript
const upgrade = require('mysql-upgrade')

const upgradeConfig = {

	// MySQL settings (passed directly to the MySQL connector) - at least user, password and database are required
	mysql: {
		host: 'localhost',
		user: 'root',
		password: '',
		database: ''
	},

	// Enable or disable logging output of the module
	// Optional, default: false
	verbose: true,

	// Name of the table that will store the database version
	// Optional, default: '_upgrade_version'
	// Set this if you already have a table '_upgrade_version' to avoid clashing
	table: 'my_upgrade_version',

	// Path where the SQL files are located
	// Optional, default: './database'
	filePath: './my-sql-files'
};

upgradeDb(upgradeConfig).then(function(upgraded) {
	console.log(upgraded);
	// { oldVersion: 0, newVersion: 1 }
})
```

## Issues
If you encounter any bugs or problems with this module, please [sumit an issue](https://github.com/primetime/node-mysql-upgrade/issues). Pull requests with bugfixes are of course welcome.
