#!/bin/bash
/bin/sleep 5
pkill Chrome
echo 'killed'
/bin/sleep 5
echo 'awoke'
open -a Google\ Chrome --args --disable-web-security --user-data-dir 'http://localhost:8000/index.html' --kiosk
echo 'brwoser open'
/bin/sleep 10
/Users/admin/installation/cliclick c:1902,20
echo 'mouse clicked'
/bin/sleep 2
echo 'end'
killall Terminal
echo 'killed terminal'
