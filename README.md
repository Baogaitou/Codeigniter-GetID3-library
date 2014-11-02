Codeigniter-Getid3-library
==========================

GetID3 Library for Codeigniter framework.Used to get audio file meta information.


###Useage

	function getId3v2($mp3) {
		define('GETID3_HELPERAPPSDIR', '/data/cache');
		require_once('getid3/getid3.php');

		$getID3 = new getID3;

		$ThisFileInfo = $getID3->analyze($mp3);
		getid3_lib::CopyTagsToComments($ThisFileInfo);
		
		$ar = array(
			'track_playtime'        => round(@$ThisFileInfo['playtime_seconds']			),
			'track_playtime_string' => @$ThisFileInfo['playtime_string'],
			'track_sample_rate'     => @$ThisFileInfo['audio']['sample_rate'],
			'track_bitrate'         => @$ThisFileInfo['audio']['bitrate']
			);

		/*
		echo round(@$ThisFileInfo['playtime_seconds']).'<br>';
		echo @$ThisFileInfo['playtime_string'].'<br>';
		echo @$ThisFileInfo['audio']['sample_rate'].'<br>';
		echo @$ThisFileInfo['audio']['bitrate'].'<br>';
		*/
		return $ar;
	}
