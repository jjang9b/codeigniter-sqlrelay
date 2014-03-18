CodeIgniter <a>Sqlrelay Adapter</a> <b>Prepare</b> <br />
    based on CodeIgniter <b>v2.1.0</b>
    <p />
    
	
	1. database.php config 
	<pre>
	<b>Application/config/database.php</b>
	
	ex)
	$db['dbsqlrelay']['hostname'] = 'hostname';
	<a>$db['dbsqlrelay']['port'] = 'portnumber';</a> 
	$db['dbsqlrelay']['username'] = 'username';
	$db['dbsqlrelay']['password'] = 'password';
	$db['dbsqlrelay']['database'] = '';
	<a>$db['dbsqlrelay']['dbdriver'] = 'sqlrelay';</a>
	<a>$db['dbsqlrelay']['dbcase'] = 'oci8';</a>
	</pre>
	
	2. Sqlrelay Adapter Add
	<pre>
	System/database/driver/<b>sqlrelay</b>
	
	- Sqlrelay_driver.php
	- Sqlrelay_result.php
	- Sqlrelay_forge.php
	- Sqlrelay_utility.php
	</pre>
	
	3. Bug? (because use sqlrelay)
	<pre>
	<b>System/database/driver/oci8/oci8_driver.php</b>
	$_commit = "";
	$escape_str ="";
	</pre>
	
	<p>&nbsp;</p>
	<p>&nbsp;</p>
	<a name="function"></a>
	<p>
    CodeIgniter <a>Sqlrelay Adapter</a> <b>Function</b>
    </p>

    1. common use
	<pre>
	<a href="http://codeigniter.com/user_guide/database/index.html" style="text-decoration:underline;" target="_blank">http://codeigniter.com/user_guide/database/index.html</a>
	use same codeigniter methods.
	</pre>
	<p>&nbsp;</p>
	
	2. function stored procedure()
	<pre>
	<b>case1. only input variable</b>
		$params = array(
			array('name'=>':variable1','value'=>'value'),
			array('name'=>':variable2','value'=>'value')
		);

		$query = $this->db->stored procedure($package, $procedure, $params);
		foreach($query->result() as $row)				<b>// return sqlrelay resource_id</b>
		{
			echo $row->colname;
		}
	
	<b>case2. output variable</b>
		$params = array(
				array('name'=>':variable1','value'=>'value'),
				array('name'=>':variable2','value'=>'<b>@out</b>')
				);
		$query = $this->db->stored procedure($package, $procedure, $params);
		<b>foreach($query as $k=>$v)</b>					<b>// return common array</b>
		{
			echo "$k / $v";
		}
	</pre>
	
	3. unsupported_function 
	<pre>
	 - function reconnect()
	 - function db_select()
	 - function db_set_charset()
	 - function insert_id()
	 - function _error_number()
	</pre>
