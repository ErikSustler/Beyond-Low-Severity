# Beyond Low Severity: The Risks of User Enumeration



# 1. Summary

User enumeration is a vulnerability that occurs when an application allows an attacker to determine whether a user has a registered account on a service. This typically happens when the application responds differently depending on whether a supplied username or email address is associated with an existing account. These differences may include error messages, HTTP status codes, response times, or other observable behavior.

Although user enumeration is often classified as a Low-severity issue due to the lack of direct unauthorized access, the information disclosed at scale can be used to build profiles of registered users. When combined with information from other publicly available sources, these profiles can help an attacker identify individuals, associate them with specific services, and establish a clearer picture of their potential targets.

This information can subsequently be leveraged to facilitate targeted phishing campaigns, credential-stuffing attempts, or other account-focused attacks. Consequently, the security implications of user enumeration extend beyond the disclosure of individual account existence and should be evaluated in the context of the information exposed, the scale of enumeration, and the potential for further exploitation.


# 2. Security Impact


The impact of user enumeration extends beyond confirming the existence of individual accounts. When an application allows accounts to be identified systematically, an attacker may be able to automate the collection of account information across multiple services and use it to build detailed profiles of individual users.

An important factor to consider is the decreasing technical barrier to developing such tools. With the assistance of publicly available AI tools, even an individual with limited programming experience, such as a novice attacker, may be able to develop a functional script for collecting, organising, and correlating account information within a relatively short period. What might previously have required a greater level of technical knowledge can now be made more accessible through AI-assisted development. Although building a reliable system still requires testing, troubleshooting, and access to suitable data sources, the overall effort required to create basic automation may be substantially reduced.

Consider an attacker attempting to gather information about a specific target. By identifying accounts associated with different services, such as a gym or a second-hand marketplace, the attacker can begin establishing connections between the target and their interests, activities, and online presence. While each individual discovery may appear insignificant, combining these findings can provide a broader picture of the target's behaviour and potentially reveal patterns in their activities.

On a larger scale, this approach can extend beyond identifying interests and activities. Depending on the services involved and the information available, an attacker may be able to infer characteristics such as age range, gender, political leanings, or other personal attributes. For example, identifying accounts across specialised websites may provide clues about a person's interests or affiliations.

The primary concern is the ability to aggregate seemingly insignificant disclosures into a more comprehensive profile. When user enumeration can be performed at scale and across multiple services, it may reduce the effort required to gather intelligence on individuals, identify potential targets, and develop more convincing social engineering campaigns. The combination of easily exploitable enumeration vulnerabilities, automated data collection, and increasingly accessible AI-assisted development can lower the barrier to conducting these activities. This transforms what may initially appear to be a minor information disclosure into a broader privacy and security concern.

# 3. Technical Analysis

User enumeration typically occurs when an application reveals whether an account exists through differences in its responses to user-supplied input. These differences may appear in registration forms, login pages, password-reset functionality, or other account-related features.

For example, when submitting an email address to a password-reset form, an application may return a message such as "An account with this email address was found" if the account exists, while returning "No account found" if it does not. Even when the messages appear similar, differences in HTTP status codes, response structure, or processing time may allow an attacker to distinguish between valid and invalid accounts.

The vulnerability becomes more significant when these responses can be reliably distinguished and the process can be repeated across a large number of potential identifiers. If the application lacks sufficient protections against automated requests, an attacker may be able to enumerate accounts systematically with relatively little effort.

The underlying issue is the application's failure to prevent unauthorised users from distinguishing registered accounts from nonexistent ones. Effective analysis should therefore establish which endpoints expose this behaviour, how reliably account existence can be determined, and what limitations or protections affect the enumeration process.


# 4. Severity Assessment

User enumeration is frequently assigned a Low severity rating because it does not directly grant an attacker unauthorised access to user accounts. However, assessing the vulnerability solely on the basis of its immediate impact overlooks the potential consequences of systematically collecting account information.

The severity should take into consideration the ease with which accounts can be enumerated, the number of affected users, the sensitivity of the information exposed, and the potential for the disclosed information to facilitate further attacks. Where enumeration can be automated and performed at scale, the cumulative impact may be significantly greater than that of an isolated disclosure.

Furthermore, the exposure of accounts belonging to privileged users or individuals associated with sensitive services may increase the risk. Confirmed account identifiers can help attackers prioritise targets, refine social engineering campaigns, and focus subsequent attacks on known users. Although these outcomes are not guaranteed by enumeration alone, they demonstrate why the vulnerability should be assessed in its broader security context.

Consequently, a Low severity rating should not be assigned solely because user enumeration does not directly compromise an account. The assessment should reflect the demonstrated exploitability, the extent of the exposure, and the realistic consequences for affected users. Where these factors establish a substantial security impact, a higher severity rating may be justified.

However, user enumeration does not inherently warrant a High severity classification. A High rating should be supported by evidence of significant impact and realistic attack conditions, assessed using an appropriate severity framework such as the Common Vulnerability Scoring System (CVSS).


.

