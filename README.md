

#!/bin/bash

threshold1=60
threshold2=90

totalmem=$( free -h | grep Mem: | awk '{ print $2 }' )
usedmem=$( free -h | grep Mem: | awk '{ print $3 }' )
freemem=$( free -h | grep Mem: | awk '{ print $4 }' )


if [ "$usedmem -lt "$threshold1" ]

then 

exit 0

	if [ "$usedmem -gte "$threshold1" ]

	then

	echo "The memory usage has reached $usedmem% on $HOSTNAME." | mail -s "Warning Memory Usage Alert" email@mine.com

	exit 1


		if [ "$usedmem -gte "$threshold2" ]

		then
	
		ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head > /tmp/20180401_10:30_memory_check_crtical.txt 
	
		file=/tmp/20180401_10:30_memory_check_crtical.txt

		echo "The memory usage has reached $usedmem% on $HOSTNAME." | mail -s "Critical Memory Usage Alert" email@mine.com

		exit 2

		fi

	fi

fi
