
To display the percentage of progress during scanning with **Nuclei**, you can use the **`-stats`** flag. Here's the command optimized for an 8 GB RAM device and includes progress statistics:

### Command:
```
nuclei -t /home/kali/.local/nuclei-templates/ -target <target> -o nuclei_results.txt -c 40 -stats
```


### Explanation:

1. **`-stats`**: Displays live statistics, including the percentage of scan completion and request rate.
2. **`-c 20`**: Limits concurrency to 40 threads, optimal for 8 GB RAM.
3. **`-o nuclei_results.txt`**: Saves the output to a file.



### For Multiple Targets with Progress Stats:
```
nuclei -t /home/kali/.local/nuclei-templates/ -list targets.txt -o nuclei_results.txt -c 40 -stats
```


