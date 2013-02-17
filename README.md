view_attachment
===============

Shell script to enable easy viewing of attachments from mutt on OS X

Purpose:  To be called by mutt as indicated by .mailcap to handle mail attachments.
#----------------------------------------------------------------------------------
#
# Function: Copy the given file to a temporary directory so mutt
#           Won't delete it before it is read by the application.
#
#           Along the way, discern the file type or use the type
#           That is given.
#
#           Finally use 'open' or 'open -a' if the third argument is
#           given.
#
#
# Arguments:
#===========
#
#     $1 is the file
#     $2 is the type - for those times when file magic isn't enough.
#                      I frequently get html mail that has no extension
#                      and file can't figure out what it is.
#    
#                      Set to '-' if you don't want the type to be discerned.
#                      Many applications can sniff out the type on their own.
#                      And they do a better job of it too.
#                      
#                      Open Office and MS Office for example.
#                      
#     $3 is open with.  as in open -a 'open with this .app' foo.xls
#
# Examples:  These are typical .mailcap entries which use this program.
#========================================================================

# Here are chunks from my original .mailcap file when I wrote view_attachment. Using Numbers, and pages
# works equally well.

# MS Excel
Application/x-msexcel; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'
Application/ms-exc; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'
Application/excel; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'
Application/msexcel; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'
Application/vnd.ms-exc; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'
Application/vnd.ms-excel; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'


# MS Word
Application/msword; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'

# MS PowerPoint
application/powerpoint; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'
application/mspowerpoint; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'
application/vnd.ms-powerpoint; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'
application/x-mspowerpoint; view_attachment %s "-" '/Applications/OpenOffice.org1.1.2/Start_OpenOffice.org.app'


# Images
Image/JPEG; view_attachment %s
Image/PJPEG; view_attachment %s
Image/PNG; view_attachment %s
Image/GIF; view_attachment %s
text/calendar; view_attachment %s ics 

# UnIdentified.
Application/octet-stream; view_attachment %s "-" 

# PDF
Application/PDF; view_attachment %s pdf
