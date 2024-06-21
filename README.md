<h1>Threat Intelligence Lab</h1>



<h2>Description</h2> 
In this walkthrough/lab scenario, I was tasked with assisting the incident response team by providing threat intelligence on a suspicious executable file on a workstation. For this lab, I was only given the SHA-256 hash of the binary. Using the hash, I began my investigation on VirusTotal, where it was evident that the binary was malware, specifically tagged as a trojan and RedLine stealer. Knowing the type of malware present on the machine, it was important to determine its DNS resolutions and IP traffic. I discovered that the malware primarily communicates with the IP address 77[.]91[.]124[.]55. Further investigation into this IP on VirusTotal revealed that it had been tagged multiple times as malicious, with community notes confirming it was seen as a command and control server for RedLine malware. Digging deeper into the malicious IP, I searched for it on AbuseIPDB and found that it is hosted by YeezyHost, a web hosting server located in Finland. With this information, the SOC team can determine if the hosting provider should be blocked altogether to enhance security against further attacks. Lastly, during the investigation, I discovered that the malware imports ADVAPI.dll, which upon further examination, is used to access registry keys and security calls, likely establishing persistence. I provided the MITRE ATT&CK technique of T1005 to assist incident responders in their report.
<br />


<h2>Utilities Used</h2>

- <b>Virus Total</b> 
- <b>AbuseIPDB</b>
- <b>MalwareBazaar</b>
- <b>Threat Fox</b>
<h2>Environments Used </h2>

- <b>Oracle Virtual Box for Kali Linux</b>

<h2>Lab Overview</h2>

The scenario for the lab:<br/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/3f0b3f89-481d-44ff-b875-f4052ccd66e1" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<br />
<br />
The file that the lab provided was a single sha256 hash value.<br/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/f8510e26-d55c-4880-95fe-676476f4a44d" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<br />
<br />
I begun my investigation by uploading the hash to VirusTotal where it was confirmed by the majority of Anti-Virus engines to be malicious. With most identifying it as a trojan/stealer. <br/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/785218c2-6f50-45dc-bb0b-2192ba64e69a" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<br />
<br />
Finding out when the malware was first seen and common names it is known as is important becasue it can change the response process if it was newly reported malware or known as a previously known malware, the eradication techniques can be significantly different.<br/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/784ff0bf-c774-4b38-a39b-648de900552a" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/e5f31f92-7bba-4695-8df7-413faca53986" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<br />
<br />
I then determined if any, what dns resolutions the stealer makes when running, and suprisingly, the one clear website was facebook.com confirmed both on Viruus Total and Joe Security Sandbox report.<br/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/8769c507-49a4-46b6-8649-6cd558797ab8" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/63001dc3-5721-45f4-869f-cf4aa94e7604" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<br />
<br />
The next piece of information is crucial, determining what IP addresses if any the malware calls back to. I discovered it to connect to 77[.]91[.]124[.]55 on the ephemeral port 19071. The IP address after further investigation was tagged as malicioius and directly as a Redline Command and Control server. <br/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/968a4f97-9f01-4581-9e90-7bb56b866113" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/5bbb24fe-762e-43c7-b5c6-878a1382d712" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/b7f3feeb-eeb1-4b02-ae1f-2ce95768e361" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<br />
<br />
If a particular hosting service is often utilized for malicious activities, the SOC team can block or restrict all traffic to and from the IP addresses associated with that hosting provider,, so I it was important to identify the hosting service of the malicious IP that the malware created the Command and Control server with. The host of the malicious IP in this case was yeezy host.<br/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/31aeb3a8-75d6-48ac-84bd-bb42077a13e3" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/13c6a755-4010-49b6-865c-8e1991f6f0cf" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<br />
<br />
WIthin scope of threat inteligence, I was able to discover the imported .dll (dynamic link library) the binary used for privilege escalation. Within Virus Total the malware was seen importing ADVAPI32.dll, and upon further research of the dll, it is used to change registry kesty and security settings within windows environments.<br/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/cce35934-4c32-40fb-b9bc-bda15eac9d7d" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/b15de092-7ac8-4e55-a0fc-01b6a0daf308" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<br />
<br />
Subsequent research on the malware, I found the primary Mitre Att&ck technique to be T1005 which usies scripting to automatically collect data on a local system, commonly used by infomation stealer and keyloggers. <br/>
<img src="https://github.com/KirkDJohnson/Threat-Intelligence-Lab/assets/164972007/62044dea-2e0f-4619-8693-f599dc30aac3" height="100%" width="100%" alt="Threat Intelligence Lab"/>
<br />
<br />



<h2>Thoughts</h2>
This lab/walkthrough was the first solely threat intelligence exercise I have done thus far. While I have plenty of experience with VirusTotal and MalwareBazaar, it has been to confirm the presence of malware in a broader investigation. In this lab, however, I was tasked with uncovering as much information about the malware as possible just from the file hash. It significantly improved my knowledge and understanding of VirusTotal, ThreatFox, and MalwareBazaar, as for many of the questions, I had to traverse multiple pages to assist the incident responders with intelligence. This was a great lab to boost my research and threat intelligence skills, both crucial for a successful SOC analyst.
