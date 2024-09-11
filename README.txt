FINAL GRADE(100)

NOTES :

	- "Server" directory contains all files relevant to the server program
	- "Miner" directory contains all files relevant to the miner program
	- "conf/mta" directory holds the "mtacoin.conf" configuration file for difficulty (set to 20)
	- Log is kept in "/var/log/mtacoin.log"

INSTRUCTIONS:

	# automated
	run the accompanied blockchain_launcher.sh script *with sudo privileges* to launch the mtacoin blockchain.
	the script will:
	* fetch the server and miner images from the docker hub repository
	* run 1 server container and 4 miner containers using a shared directory
	* ask whether to tail the server's container blockchain log
	
	# manually
	* fetch the server and miner images from the repository
		-- sudo docker image pull commissi0n/mtacoin-server:1.0
		-- sudo docker image pull commissi0n/mtacoin-miner:1.0
	* run the server container with a shared volume (directory of the "mtacoin.conf" file)
		-- sudo docker run -d -v ./conf/mta/:/mnt/mta/ commissi0n/mtacoin-server:1.0
	* run the miner container with the same shared volume
		-- sudo docker run -d -v ./conf/mta/:/mnt/mta/ commissi0n/mtacoin-miner:1.0
		
	*Server container should run first

	*Server reads difficulty from the "mtacoin.conf" file (expected format: "DIFFICULTY=X")

	*0<=DIFFICULTY<=31

	*Maximum of 4 miner containers at once

	*If no "mtacoin.conf" file is present difficulty will be set to default (16)


