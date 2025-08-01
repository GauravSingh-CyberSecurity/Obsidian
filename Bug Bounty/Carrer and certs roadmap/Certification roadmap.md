
==Certification sequence:==
==First get HTB CBBH cert== 
==OSWA==
==OSCP== (Rana Khalil, TJnull's list )
==OSWE== ( TJnull's list , Download 10-20 exam VAPT reports for OSWE created by people who completed it i.e "OSWE exam report")

```
Tj null list for OSWE | OSCP

https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://docs.google.com/spreadsheets/u/1/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/htmlview&ved=2ahUKEwjF0tOBg-qOAxWq9DgGHU7lFZQQjjh6BAhZEAE&usg=AOvVaw3DqRsG_eVMArO8bCjxxLx3
```

lists and related materials for Offensive Security (OffSec) certifications.

**Tj Null's Lists**
Tj Null is well-known in the community for curating lists of vulnerable machines from platforms like Hack The Box (HTB) and OffSec's Proving Grounds. These are not official OffSec resources, but they are widely used by students to prepare for their exams. The main lists are for:
 * OffSec Certified Professional (OSCP): This is the most famous of Tj Null's lists. It provides a curated set of machines from various platforms that are considered to be representative of the skills and difficulty level required for the OSCP exam. It's often broken down by difficulty (easy, medium, hard, etc.) and is a go-to resource for many aspiring pentesters.
 * OffSec Experienced Penetration Tester (OSEP): This list is for those preparing for the more advanced OSEP certification, which focuses on advanced penetration testing techniques.
 * OffSec Web Expert (OSWE): This list is specifically for the OSWE exam, which is a highly technical certification for web application security.
 
Other Study Materials and Resources
While Tj Null's lists are a great starting point, the cybersecurity community has developed a vast amount of other resources to help with OffSec certifications. These include:
 * **Official OffSec Course Materials:** This is the primary and most important resource. The courses themselves (e.g., PEN-200 for OSCP, WEB-300 for OSWE, etc.) and the associated lab environments are the core of the preparation.
 * **Walkthroughs and Write-ups**: Many people, including content creators like IppSec and bloggers, create detailed walkthroughs and write-ups for the machines on Tj Null's lists. These are invaluable for learning new techniques and understanding how to solve a machine.
 * **Community Forums and Discord Channels**: Platforms like Reddit's r/oscp and various Discord channels are places where students can ask questions, discuss methodologies, and get support from other people on the same journey.
 * **Cheat Sheets and Guides**: People often create their own personal notes, cheat sheets, and methodology guides for different phases of a penetration test (e.g., enumeration, privilege escalation). There are many publicly available examples of these resources.
 * **HTB Academy and Proving Grounds**: These platforms provide a structured learning path with hands-on labs that are often used in conjunction with the official OffSec materials. The machines from these platforms are frequently included in Tj Null's lists.
 *  **Read OSWE exam report of people who completed it and submitted the vapt report**

It's important to note that "dumps" (i.e., memorized exam questions and answers) are generally considered unethical and are against OffSec's policies. The community strongly discourages using them, as the goal of the certifications is to test one's ability to think like a professional, not to memorize solutions. The focus is on learning the fundamental skills and methodology, which is what Tj Null's lists and other community resources are designed to help with.





r/OSWE :`https://www.reddit.com/r/OSWE/comments/1dmv16a/oswe_exam/`

Asleep-Whole8018

1y ago
You need to do more research, but here's the gist: In the test, you've got two machines/source code to tackle. First, find and exploit authentication bypass and remote code execution (RCE) on both. You'll also need to script it (probably in Python, but any language works) to nail both objectives without any extras. Your report should include code analysis, reviews, and the script. To pass, you need 85 points: one machine with full authentication bypass + RCE, and on the other, at least authentication bypass.


---



..
#### **1️⃣2️⃣ Should CBBH holders target OSWA & OSWE first or OSCP?**

- **If you want to specialize in ==Web Security & Bug Bounty:**== → **CBBH → OSWA → OSWE → (Optional) OSCP**
- **If you want to be a ==Penetration Tester:**== → **CBBH → OSWA → OSCP → (Optional) OSEP**
- **If you want to be a ==Full-Stack Offensive Security Expert:**== → **CBBH → OSWA → OSCP → OSWE**







---

---

#### **1️⃣ How long is the HTB CBBH exam?**

- The **HTB Certified Bug Bounty Hunter (CBBH)** exam duration is **24 hours**, followed by **48 hours for report submission**.
- It is **fully practical**, meaning you need to **hack real-world-style web applications** rather than answering MCQs or scenario-based questions.

#### **2️⃣ What is the pass rate for CBBH?**

- HTB has not officially published pass rates.
- Based on community feedback, **estimated pass rate is 50-60%**.
- Success depends on your **web security experience and ability to write a clear pentest report**.

#### **3️⃣ How much preparation time is needed for CBBH?**

- If you have **basic bug bounty experience**: **2-3 months**.
- If you are **new to web security**: **4-6 months**, with lab practice and studying OWASP Top 10.
- The **HTB Academy labs are not mandatory**, but highly recommended for success.

#### **4️⃣ Is a course completion certificate provided for CBBH?**

- Yes, **HTB provides a course completion certificate** if you finish the CBBH training, even before passing the exam.
- The **official CBBH certification** is awarded **only after passing the exam**.

#### **5️⃣ CBBH vs OSCP – Prestige Level**

- **OSCP is far more prestigious and well-recognized** in the cybersecurity industry.
- **CBBH is beginner-friendly, whereas OSCP is an industry-standard certification for penetration testers**.
- If you’re planning to become a professional pentester, OSCP is a stronger certification.

#### **6️⃣ CBBH vs OSWA – Prestige Level**

- **OSWA (Offensive Security Web Assessor) is more advanced than CBBH**.
- **CBBH is an entry-level web security certification, whereas OSWA focuses on in-depth manual web testing and OffSec methodologies**.
- If you want to specialize in web security, **OSWA is a great next step after CBBH**.

#### **7️⃣ OSWA vs OSCP – Prestige Level**

- **OSCP is far more prestigious** because it covers **network, web, and privilege escalation**.
- **OSWA is focused only on web application security** and is easier than OSCP.
- If you’re aiming for a penetration testing career, **OSCP is the better choice**.

#### **8️⃣ OSCP vs OSWE – Prestige Level**

- **OSWE (Offensive Security Web Expert) is harder and more specialized than OSCP**.
- **OSCP covers general penetration testing, while OSWE focuses on white-box web application testing and source code review**.
- If your goal is **web security and bug bounty**, OSWE is more relevant.
- If your goal is **general penetration testing or red teaming**, OSCP is better.

#### **9️⃣ After CBBH, should I take OSWA or OSWE?**

- If you’re **new to OffSec certifications**, **OSWA is the best next step after CBBH**.
- **OSWE is much harder** and requires **source code review skills**.
- If you already have **coding experience (Python, JavaScript, PHP)** and **strong bug bounty experience**, you can **skip OSWA and go directly to OSWE**.

#### **🔟 How much preparation time is needed for OSWA after CBBH?**

- If you’re **a beginner**: **3-4 months**.
- If you’re **an intermediate bug bounty hunter**: **1-2 months**.
- If you’re **already skilled in web security**: **2-4 weeks**.

#### **1️⃣1️⃣ How much preparation time is needed for OSWE after CBBH?**

- If you’re **a beginner with no coding experience**: **6-9 months**.
- If you’re **intermediate with some bug bounty & coding knowledge**: **4-6 months**.
- If you’re **advanced with strong scripting & web security skills**: **2-3 months**.

#### **1️⃣2️⃣ Should CBBH holders target OSWA & OSWE first or OSCP?**

- **If you want to specialize in Web Security & Bug Bounty:** → **CBBH → OSWA → OSWE → (Optional) OSCP**
- **If you want to be a Penetration Tester:** → **CBBH → OSWA → OSCP → (Optional) OSEP**
- **If you want to be a Full-Stack Offensive Security Expert:** → **CBBH → OSWA → OSCP → OSWE**

---

### **Recommended Roadmap for Career & Skill Growth (Chronological Order)**

---

### **Final Takeaways**

🔥 **If you're fresh out of CBBH, start with OSWA before jumping into OSCP or OSWE.**  
🔥 **If you have strong web security skills, you can go straight to OSWE after OSWA.**  
🔥 **OSCP is best done before OSWE for overall offensive security expertise.**

💡 **This roadmap ensures steady career and skill growth while avoiding burnout.** 🚀

---

