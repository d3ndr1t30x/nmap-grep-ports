# nmap-grep-ports
Handy bash one liner to grep all port numbers from an Nmap output file and print them to a single line for further scanning.

```cat nmap/scan1.nmap | grep -oP '^\d+/tcp' | awk -F/ '{print $1}' | tr '\n' ',' | sed 's/,$/\n/'```

Breakdown of the Command:

```cat nmap/scan1.nmap```: Reads the Nmap output file.
```grep -oP '^\d+/tcp'```: Uses grep with Perl-compatible regex (-P) to extract lines starting with port numbers followed by /tcp.
```awk -F/ '{print $1}'```: Splits the output by / and prints the first part (the port number).
```tr '\n' ','```: Translates newlines into commas.
```sed 's/,$/\n/'```: Uses sed to remove the trailing comma and replace it with a newline.

Example Output:

For the given input, the command will output:

```21,22,23,25,53,80,111,139,445,512,513,514,1099,1524,2049,2121,3306,3632,5432,5900,6000,6667,6697,8009,8180,8787,38405,45023,46534,47247```


