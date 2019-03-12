#!/bin/bash

##################################################
# Kirby Campbell
# 09 Mar 2019
# This program will greet user
# and provide a menu of options
# for common UNIX actions.
# WMorales CS140U
##################################################

user_response = "z"  # initialize user_response to an unused char so loop will run
clear

until [ "$user_response" = "j" ] # j will exit program / Loops until j is pressed
	do # Do the following each time user_response is anything but j
		echo "###############################################################"
		echo "~~~Hello there User!~~~"
		echo
		echo "Welcome to Unix Menu Machine"
		echo
		echo "Choose from the following items: "
		echo " a). Email Composition "
		echo " b). List of logged in users "
		echo " c). Print Current Date & Time "
		echo " d). Print Calendar of this month "
		echo " e). Print name of working directory "
		echo " f). Print contents of working directory "
		echo " g). Find the IP of a web address "
		echo " h). ~~See UNIX fortune teller ~~"
		echo " i). Print a file (on screen) "
		echo " j). Exit this program "
		echo " ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ "
		echo
		echo "  ~ Please select a letter ~ "
		echo
		echo -n "Your Response: "
		echo
		read -n1 user_response # Program waits for user's key press

	################################################################

		case $user_response in # Begins user input case outcomes

	###############################################################

		a|A) # When a or A is pressed - do the following
			clear
			echo "~~ Email Composition Program ~~ "
			echo
			echo -n "Enter your Email subject and press <enter>: "
			read email_subject # Waits for user to enter email subject
			echo
			echo -n "Enter your recipient's address then press <enter>: "
			read email_address # Waits for user to enter email address
			echo
			echo -n "Attach file by entering file path and press <enter>: "
			read email_attach # Waits for user to attach a file
			mail -s "$email_subject" "$email_address" < "$email_attach" # Uses mail command to send attachment to the email address with the given subject - by using each variable that the user typed into
			clear
			echo "Your message has been sent to $email_address successfully! "
			sleep 2 # Sleeps to remove clutter and draw focus to success message
			clear 
			;;
	################################################################

		b|B) # When b or B is pressed  - do the following
			clear
			echo "You've chosen to Print a list of Users currently logged in!"
			echo
			echo "Logged in Users: "
			who | more # Who lists all users currently logged on & more gives expanded info on them
			echo
			sleep 1 # Wait 1 second before returning to main menu
			;;
	################################################################

		c|C) # When c or C is pressed - do the following
			clear
			echo " You've chosen to print todays date and time! "
			echo
			date # date outputs todays date and time
			sleep 1
			echo
			;;
	################################################################

		d|D) # When d or D is pressed - do the following
			clear
			echo " You've chosen to print this month's calendar! "
			echo
			cal # cal outputs the current month
			sleep 1
			echo
			;;
	###############################################################

		e|E) # When e or E is pressed - do the following
			clear
			echo "You've chosen to print the current working directory name! "
			echo
			pwd # pwd outputs the current working directory's name
			sleep 1
			echo
			;;
	################################################################

		f|F) # When f or F is pressed - do the following
			clear
			echo " You've chosen to print the contents of the current working diectory! "
			echo
			ls # ls outputs the list of all items in the current working directory
			sleep 1
			echo
			;;
	################################################################

		g|G) # When g or G is pressed - do the following
			clear
			echo " Let's Search for the IP address of a web address! "
			echo
			echo -n "Enter the Web Address you'd like to search for and press <enter>: "
			read web_address # Waits for user to enter a web address and assigns it to web_address variable
			host "$web_address" # host outputs the IP info for the given web address
			echo
			sleep 1
			;;
	#################################################################
	
		h|H) # When h or H is pressed - do the following
			clear
			echo " ~~Let's look into my crystal ball ~~" # Begin creepy text sequence
			echo
			sleep 1 # Create space between each creepy component
			echo " ** Mysteriously rubs crystal ball **"
			sleep 1
			echo
			echo "          ** Lights Dim ** "
			sleep 1
			echo
			echo "   ** You Feel a rush of cold air ** "
			sleep 1
			echo
			echo "           Your fortune is: "
			echo
			fortune # fortune outputs random fortunes from within the UNIX system
			echo
			sleep 1
			;;
	################################################################

		i|I) # When i or I is pressed - do the following
			clear
			echo " You've chosen to print a file to the screen! "
			echo
			echo "Please Enter the Path of the file to print then press <enter>: "
			echo
			echo "###  Note: Enter either a file name like sample.txt"
			echo "###          OR Enter the full address like:"
			echo "###             /home/student/user.name/sample.txt"
			echo
			read file_path	# Waits for user to enter a file path and assigns it to file_path variable
			echo
				if [ -f "$file_path" ] # if file_path is actually a file path
					then #if the above statement is true - do the following
						more "$file_path" # cat outputs the contents of the given file path
				else # if file_path is not actually a file then do the following
					echo "Error... No file found at that path.  Please try again! " #outputs when no file path was entered
				fi # ends the if statement
			echo
			;;
	################################################################

		j|J) # When j or J is pressed - do the following
			clear
			echo "Shutting Down this Program" #Friendly Ending sequence
			sleep 1
			echo "GoodBye Mr/Ms User!"
			sleep 2
			break;; # Break leaves the program altogether

	################################################################

		*) # When any key that is not a-j or A-J is pressed - do the following
			clear
			echo "Invalid Menu Option."
			echo "Please choose a valid menu option! "	
			echo
			;;

	
		esac # esac is the end of a case block
	done # end of loop
