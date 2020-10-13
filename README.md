# Bash_cheatsheet
Useful tricks I always needs, I'm always searching and finding them hours after...


# Bash shell in OSX:

### Add newlines after a pattern

    sed 's/XXX/XXX\'$'\n/g' file > file_02
ex:

    sed 's/Control_3_30c/Control_3_30c\'$'\n/g' file > file_02

### Add a line a the top of a file, with tabulation within:

    sed $'1s/^/ZZZa\tYYYb\tXXX/' file > file_02
ex:

    sed $'1s/^/Acclimation_1_31_5a\tAcclimation_1_31_5b\tAcclimation_1_31_5c\tAcclimation_3_30a\tAcclimation_3_30b\tAcclimation_3_30c\tControl_1_30a\tControl_1_30b\tControl_1_30c\tControl_3_30a\tControl_3_30b\tControl_3_30c/' file > file_02


### Obtain count, min and max for each unique entry, useful for obtainning genes lengths from only an exon database:

    awk '{
      count[$1]++
      min[$1]=(!($1 in min) || $2<min[$1]) ? $2 : min[$1]
      max[$1]=(!($1 in max) || $3>max[$1]) ? $3 : max[$1]
    }
    END {
      print "Name","Count","Minimum","Maximum"
      print "----","-----","-------","-------"
      for(i in count) print i,count[i],min[i],max[i]
    }' input_file > output_file | column -t


### Known how many same genes are into same cluster (here, if only two replicate)

    awk 'seen[$0]++ && seen[$0] == 2' 
