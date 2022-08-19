# Random Cards
Random Selection Cards

Copy and run in local - PHP language

```
<!DOCTYPE html>
<html>
	<body>
		<head>
			<title> Random Card </title>
			<style type="text/css">
				 div{margin: 15px 0;}
				 /*font{border: 1px solid #ccc;padding: 6px 3px; margin-right: 10px;}*/
			</style>
			
			<script>
				function clicked(){
					var num = document.getElementById('number');
					
					if(num.value == ''){
						alert('Please insert any number..');
						return false;
					}
					
					if(num.value == 0 || num.value > 4){
						alert('Please insert a valid number (1-4)');
						return false;
					}
				}
			</script>
		</head>

		<h2>Random Card</h2>
		
		<?php 
			if (isset($_POST['number'])){
			//include 'card.php';	
			
			$num = $_POST['number'];
			$sp = poker();
			$sp2 = poker2();
			for($a=1; $a <= $num; $a++){
		?>
		
			<div> Player <?php echo $a;?> card -> 
				<?php
					 
					/* for ($i=1; $i <=13 ; $i++) { 
						 echo current($sp);
						 next($sp);
					} */
					
					for ($i=1; $i <=13 ; $i++) { 
						 echo current($sp2);
						 $i < 13 ? print(','):print('');
						 next($sp2);
					}
				?>
			</div>
			<?php 
				}
			}
			?>
		<font style='border: 1px solid #ccc;padding: 6px 3px; margin-right: 10px;'>
			S = ♠, <span style='color:red;'>H = ♥</span>, C - ♣, <span style='color:red;'>D = ♦️</span>
		</font>
		<form action="<?php echo $_SERVER['PHP_SELF'];?>" method='post' onsubmit='return clicked();'>
			<div>
				<input type='number' placeholder='insert number' name='number' style='text-align:center;width:130px; height:85px;' id='number' value='<?php if (isset($_POST['number'])){ echo $_POST['number'];}?>'>
			</div>
			<font color='red'><small>#Invalid No = 0, 5 and above</small></font>
		<br/>
		<br/>
		<input type='submit' value='Submit'>
		</form>
	</body>
</html>

<?php 
	function poker(){
		 //Set up an array to save the deck
		 $num = ['A','2','3','4','5','6','7','8','9','10','J','Q','K'];
		 $icon = ['♥'=>'red','♦️'=>'red','♠'=>'black','♣'=>'black'];
		 //Generate deck
		 foreach ($icon as $key => $vi) {
			 foreach ($num as $vn) {
			  $poker[] = "<font style ='color:$vi;'> $vn $key </font>";
			 }
		 }

		 Shuffle ($poker); // shuffle
		 return $poker;
	}
	
	function poker2(){
		 //Set up an array to save the deck
		 $num = ['A','2','3','4','5','6','7','8','9','10','J','Q','K'];
		 $icon = ['H'=>'red','D'=>'red','S'=>'black','C'=>'black'];
		 //Generate deck
		 foreach ($icon as $key => $vi) {
			 foreach ($num as $vn) {
			  $poker[] = "<font style ='color:$vi;'> $vn-$key </font>";
			 }
		 }

		 Shuffle ($poker); // shuffle
		 return $poker;
	}

?>
```
