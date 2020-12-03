## 11/28/2020:
1. **Typosquatting** (AKA URL Hijacking): This is a form of cybersquatting (sitting on sites under someone else's brand     or copyright) that targets Internet users who **incorrectly type a website address into their web browser** (eg "Gooogle.com" instead of "Google.com)
 - https://www.mcafee.com/blogs/consumer/what-is-typosquatting/
> To protect your self against typosquatters, pay close attention to the spelling web addresses and test the validit    y of the site (ie look for features and characteristics of the site that are out of the norm).
2. Session hijacking == Cookies hijacking
3. **Port Mirroring** (AKA SPAN/Switched Port Analyzer): A method of monitoring network traffic that enables you to send     copies of all network packets from one port to another port (ie where the packet can be analyzed).
 - https://community.fs.com/blog/port-mirroring-explained-basis-configuration-and-fa-qs.html
4. SIEM vs IDS:
 - The main difference between SIEM and an IDS is that SIEM tools allow the user to **take preventive action against     cyberattacks** whereas an IDS only detects and reports events.
 - https://purplesec.us/siem-vs-ids/#:~:text=An%20Intrusion%20Detection%20System%20(IDS,only%20detects%20and%20reports%20events.
5. Linux Devices (@Linux-Devices.md)

## 11/29/2020:
1. **Linux Plan**: You can document plans for yourself using the .plan file
```bash
$ finger <user>
Login: <user>                         Name:
Directory: /home/<user>               Shell: /bin/bash
Last login Tue Nov 24 14:26 (EST) on pts/0 from <host address>
No Mail.
No Plan.
```
As you can see on the bottom, it states "No Plan" which means that you can setup plans for yourself. This is through the .plan file. Once you type something in that file, that information will display there.

2. **Buffer Overflow**: A condition in which a running program attempts to write data outside of a temporary data storage area (known as a **buffer**) and into other areas of program memory not intended to store this data. Also called a **buffer overrun**.

3. **Buffer Overflow vs Overrun**:
 - A **buffer overrun** is when you are iterating over the buffer and keep reading past the end of the array
 - A **buffer overflow** is when you try to put more items in the array than the array can hold.

4. Underflows & Underruns: This typically occurs when the temporary holding space during data transfer ([buffer](https://whatis.techtarget.com/definition/buffer)) is fed at a lower rate than it is being read from. As a result, the data is underflowing the preceding pieces of data.

5. Misconception I had with denial of service: Denial of services are not only caused by hundreds of botnets pinging one victim, but also from buffer overflows. Denial of services can be caused from something as simple as unplugging the server's power outlet.
 - There are two types of denial of services: local and remote denial of service
