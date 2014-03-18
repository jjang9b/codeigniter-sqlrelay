CodeIgniter Sqlrelay Adapter Prepare
based on CodeIgniter v2.1.0


1. database.php config 

 Application/config/database.php


    	$db['dbsqlrelay']['hostname'] = 'hostname';
    	$db['dbsqlrelay']['port'] = 'portnumber';
    	$db['dbsqlrelay']['username'] = 'username';
    	$db['dbsqlrelay']['password'] = 'password';
    	$db['dbsqlrelay']['database'] = '';
    	$db['dbsqlrelay']['dbdriver'] = 'sqlrelay';
    	$db['dbsqlrelay']['dbcase'] = 'oci8';


2. Sqlrelay Adapter Add

 System/database/driver/sqlrelay

- Sqlrelay_driver.php
- Sqlrelay_result.php
- Sqlrelay_forge.php
- Sqlrelay_utility.php


3. Bug? (because use sqlrelay)

 System/database/driver/oci8/oci8_driver.php
 
 	`$_commit = "";`
 	
	`$escape_str ="";`



CodeIgniter Sqlrelay Adapter Function
-


1. common use

 http://codeigniter.com/user_guide/database/index.html
 use same codeigniter methods.

2. function stored procedure()

 case1. only input variable

		$params = array(
			array('name'=>':variable1','value'=>'value'),
			array('name'=>':variable2','value'=>'value')
		);
		
		$query = $this->db->stored procedure($package, $procedure, $params);
		foreach($query->result() as $row)			// return sqlrelay resource_id
		{
			echo $row->colname;
		}

 case2. output variable

		$params = array(
				array('name'=>':variable1','value'=>'value'),
				array('name'=>':variable2','value'=>'@out')
				);
		$query = $this->db->stored procedure($package, $procedure, $params);
		foreach($query as $k=>$v)				// return common array
		{
			echo "$k / $v";
		}


3. unsupported_function 

	- function reconnect()
	- function db_select()
	- function db_set_charset()
	- function insert_id()
	- function _error_number()

