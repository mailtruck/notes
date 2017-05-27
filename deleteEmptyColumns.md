To run this script, simply open up a terminal in Linux and type –

perl deleteEmptyColumnsFromCSV.pl Input_CSV_Filename Output_Filename

Substitute Input_CSV_Filename with the name of the CSV file from which you want empty columns to be removed and Output_Filename with name of the file to which the output needs to be written.

> https://www.netiq.com/communities/cool-solutions/cool_tools/delete-empty-columns-csv-file/

```
#!/usr/bin/perl
#use warnings;
use strict;

my $line;
my $file = $ARGV[0];
my $outfile = $ARGV[1];
my @headercolumns;
my @headervalues = ();
if($#ARGV +1 != 2) {
die("Usage InputCSVFile OutputFile");
} 
open (FILE, $file) or die ("Could not open $file!");
#Get Column Headers
$line = <FILE>;
chomp $line;
@headercolumns = split(',',$line);
my $columncount = scalar(@headercolumns);
my $rowcount = 0;
for (my $count = 0; $count <= $columncount ; $count++){
     my @temparray = $headercolumns[$count];
     push @{ $headervalues[$count] }, $headercolumns[$count];
}

#read the file line by line and add it to array 
while ($line = <FILE>)
{
  chomp $line;
  $rowcount++;
  my @quote_positions = split('"',$line);
  my $array_size = scalar(@quote_positions);
  #Check if there are any escaped values
  if($array_size>1) {
    my $count = 0;
    for (my $i = 0; $i < $array_size; $i++) {
       my $string = $quote_positions[$i];
       if(($i % 2) == 0) {
         my $pos = index ($string,',');
    #Don't chop , if first element in array
         if($pos == 0 && $i != 0 ) {
    #Don't chop , if its last element in array and its the only character
           if(!($i == $array_size-1 && length($string) == 1)) {
             $string =~ s/,//;
           }  
         }
    #Chop the last extraneious , in the array element but not for last element in array 
        if($i != $array_size -1 && length($string) > 1) {
          chop($string);
        }
        if($string) {
          my @columns = split(',',$string);
          my $comma_count = ($string =~ tr/,//);
          my $j = 0;
    #Special case where you get a string of two consecutive commas
          if($comma_count == 1) {
            $j = 1;
          }
          for (; $j <= $comma_count ; $j++){
             if(trim($columns[$j])) {
               $headervalues[$count][$rowcount] = $columns[$j]; 
             }
             $count++;
          }
       }
     } else {
           $headervalues[$count][$rowcount] = "\"".$string."\"";
           $count++;
       }
    }
  } else {
        my @columns = split(',',$line);
        for (my $count = 0; $count <= $columncount ; $count++){
           if(trim($columns[$count])) {
             $headervalues[$count][$rowcount] = $columns[$count]; 
           }
        }
    }
}

open (OFILE, ">>$outfile");

#Find out which columns are empty
my @emptycolumns;
for (my $count = 0; $count <= $columncount ; $count++){
    if(scalar(@{$headervalues[$count]}) <= 1) {
      $emptycolumns[$count] = 1;
    }
}

#Write to a new file
my $count = 0;
my $rcount = 0;
my $first = 1;
for ( $rcount = 0; $rcount <= $rowcount ; $rcount++){
    $first = 1;
    for ( $count = 0; $count <= $columncount ; $count++){
#Write column only if its not empty
        if($emptycolumns[$count] != 1) {
          if($first != 1) {
            print OFILE ",";
          } 
          if($headervalues[$count][$rcount]) {
             print OFILE $headervalues[$count][$rcount];
          } else {
             print OFILE ""; 
          }  
          $first = 0;
        }
   }
   print OFILE "\n";
}

# Perl trim function to remove whitespace from the start and end of the string
sub trim($)
{
        my $string = shift;
        $string =~ s/^\s+//;
        $string =~ s/\s+$//;
        return $string;
}
```