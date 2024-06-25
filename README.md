# ffuf_Cookbook
Ffuf tool A high-speed web fuzzer developed in Go.FFUF is one of the newest and fastest open-source fuzzing tools available. But before we dive in, let's understand what fuzzing is.

Fuzzing is the process of automatically providing random input to an application to find errors or unexpected behavior. It can also involve discovering hidden directories and files on a web server. FFUF is the automated tool developed in the Golang language which is the fastest fuzzer tool in today’s date. It has various key features of manipulation the method from GET to POST and vice versa. We can use various wordlists for fuzzing the vhost as well. FFUF tool is an open-source and free-to-use tool.

1)How to install fuff in kali linux:

Commmand: sudo apt-get install fuff

![image](https://github.com/poojitha6104/ffuf_Cookbook/assets/141235417/0bd0cefa-38e5-49fc-abd6-4f853666e4a2)

2)Usage with the command ffuf -h. We can find the help page we can explore the tool with this command
![image](https://github.com/poojitha6104/ffuf_Cookbook/assets/141235417/169ed21d-a48a-4b37-a263-090ca7e810ec)


3)ffuf offers many options for fuzzing.

To specify the position to be fuzzed, use the word "FUZZ" in the ffuf command.

Directory and File Discovery You can find directories on a website with the following command. It uses the -w flag to provide a wordlist and the -u flag to specify the URL with "FUZZ" as the placeholder for fuzzing.

ffuf -w wordlist.txt -u http://website.com/FUZZ

For file discovery, you can use the same command. To include specific file extensions from the wordlist, use the -e flag.

ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html,.php,.txt
![image](https://github.com/poojitha6104/ffuf_Cookbook/assets/141235417/03f8ba03-a1f2-4e22-bf57-9d70ad06dab5)


image ffuf offers options to filter responses by specific status codes, line counts, response sizes, word counts, and regex patterns.

Filtering Options -mc: Status code -ml: Number of lines in the response -mr: Regex pattern -ms: Response size -mw: Number of words in the response

4)Examples:

To get responses with status codes 200 and 302, use: Command : ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html -mc 200,302 Recursion

URL parameters ending with FUZZ support recursion. The -recursion flag activates this, allowing ffuf to fuzz URLs and then fuzz further within the directories it discovers. -recursion-depth: Specifies the depth of recursion -maxtime: Sets a maximum time in seconds for the fuzzing process -maxtime-job: Used with -recursion to set a maximum time for each new job created per directory found

Example:

Command: ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u https://geeksforgeeks.org/FUZZ

In this example, We are fuzzing the directories of geeksforgeeks.org target domain.

![image](https://github.com/poojitha6104/ffuf_Cookbook/assets/141235417/0efe88f6-d6d4-4396-af68-94d58547d6f3)

Example for a maximum fuzzing time of 60 seconds:

ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u https://geeksforgeeks.org/FUZZ -maxtime 60

![image](https://github.com/poojitha6104/ffuf_Cookbook/assets/141235417/25b927a1-7eb0-4bc2-a0cb-5a3a09746961)
