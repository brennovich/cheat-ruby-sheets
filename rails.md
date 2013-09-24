# Default Directory Structure
`
rails_root  
|-- app  
|   |-- assets  
|   |-- controllers  
|   |   |-- application.rb  
|   |-- helpers  
|   |   |-- application_helper.rb  
|   |-- models  
|   |-- views  
|       |-- layouts  
|-- components  
|-- config  
|   |-- enviroments  
|   |   |-- development.rb  
|   |   |-- production.rb  
|   |   |-- test.rb  
|   |-- database.yml  
|   |-- enviroment.rb  
|   |-- routes.rb  
|-- db  
|-- doc  
|-- lib  
|-- log  
|   |-- development.log  
|   |-- production.log  
|   |-- server.log  
|   |-- test.log  
|-- public  
|-- script  
|-- test  
|   |-- fixtures  
|   |-- functional  
|   |-- mocks  
|   |-- unit  
|   |-- test_helper.rb  
|-- vendor  
`
# Methods
### Strings
capitalize!  
center  
chomp!  
chop  
concat  
count  
crypt  
delete!  
downcase!  
dump  
each  
each_byte  
empty?  
gsub!  
hash  
hex  
include?  
index  
intern  
length  
|just, rjust  
next!  
oct  
replace  
reverse!  
rindex  
scan  
slice!  
split  
squeeze!  
strip!  
sub!  
sum  
swapcase!  
tr!  
tr_s  
unpack  
upcase!  
upto  

### Regex
escape  
last_match  
new  
quote  
casefold?  
kcode  
match  
source  
### Time
asctime    
ctime  
day  
gmt?  
gmtime  
hour  
isdst  
localtime  
mday  
min  
mon  
month  
sec  
strftime  
tv_sec  
tv_usec  
usec  
utc  
utc?  
wday  
yday  
year  
zone  
### Arrays
assoc  
at  
clear  
collect!  
compact!  
concat  
delete  
delete_at  
delete_if  
each  
each_index  
empty?  
eql?  
fill  
first  
flatten!  
include?  
index  
indexes  
join  
last  
length  
nitems  
pack  
pop  
push  
rassoc  
reject!  
replace  
reverse!  
reverse_each  
rindex  
shift  
slice!  
sort!  
uniq!  
unshift  

### Validation
condition_block?  
create!  
evaluate_condition  
validate  
validate_on_create  
validate_on_update  
validates_acceptance_of  
validates_associated  
validates_confirmation_of  
validates_each  
validates_exclusion_of  
validates_format_of  
validates_inclusion_of  
validates_length_of  
validates_numericality_of  
validates_presence_of  
validates_size_of  
validates_uniqueness_of  

### Enumerable Mixin
collect  
each_with_index  
entries  
find  
find_all  
grep  
include?  
max  
min  
reject  
sort  

# Pre-defined Variables
$! Exception information  
$& String of last match  
$` String left of last match  
$' String right of last match  
$+ Last group of last match  
$N Nth group of last match  
$= Case insensitive flag  
$/ Input record separator  
$\ Output record separator  
$, Output field separator  
$. Current line number of last file read  
$> Default output for print  
$_ Last input line of string  
$0 Name of script  
$* Command line arguments  
$stderr Standard error output  
$stdin Standart input  
$stdout Standart output  
$-a True if -a is set.  
$-d Status of -d switch  
$-l True if -l is set  
$-p True if -p is set  
$-v Verbose Flag  

# Reserved Words
begin  
elsif  
rescue  
=end  
end   
retry  
BEGIN  
ensure  
return  
END  
false  
self  
alias  
for  
super  
and  
if  
then  
begin  
in  
true  
break  
module  
undef  
case  
next  
unless  
class  
nil  
until  
def  
not  
when  
defined?  
or  
while  
do  
redo  
yield  
else  

# Regular Expression Syntax

^ Start of string  
$ End of string  
. Any single character  
(a|b) a or b  
(...) Group section  
[abc] Item in range (a or b or c)  
[^abc] Not in range (not a or b or c)  
a? Zero or one of a  
a* Zero or more of a  
a+ One or more of a  
a{3}   
test  
Exactly 3 of a  
a{3,} 3 or more of a  
a{3,6}  
Between 3 and 6 of a  
!(pattern) "Not" prefix. Apply rule when URL does not match pattern.  
