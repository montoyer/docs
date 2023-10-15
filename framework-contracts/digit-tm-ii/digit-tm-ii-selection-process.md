---
description: >-
  The process from the request issued by the European Commission until a
  consultant starts working
---

# DIGIT TM II selection process

## Process description

<figure><img src="../../.gitbook/assets/swimlanes-989509df87bb71db3cd290aba95a1ea2.png" alt=""><figcaption><p>DIGIT TM Selection process</p></figcaption></figure>

{% embed url="https://swimlanes.io/#nVLBatwwEL3rK945sIY0PZnSS1KKQxpKs+21aO3xdoI9cqXxdpfSf6+0613LIVAoGCPNvNG8eW+UtaMSd9XHao31J1QVAnVUKzvB4F1NIcCY7yWurq4LPNhR6h+IF/PhK5Rsj9V73DoJziuPfYkv9HOkoEacUmlW+Oxdyx3F0wPtqIO3sk23J7Ve0VhNl8ex35CHa2PgEGLgjjrekT+gdw1N7d8UWaOMZSJjssy7I6N+sHJAGU9dAuL2W46JkDP/MlEcXCDUVhpOjIIx3Jao2pi0io5sUFzPeXBAGFntJg4GLJQ4961kx5q9idZ5sCj5HdOvWHWGpqoLqMSjU24Pc8hQF6JB6R+z4v7NYp/LlAx5TvMPxyFtlyMX1uHiXdRWFOogtNcMEUvjVxRFid+tDaswsAj5P7jBZgwsaVWSf+jtHkP0c1lK0kxO3hTZyLOR0cc5fHJofXLo3rFk4pmjMzM27tr0DDXmv6ebJH7JLH9yuVjSsu9nP7IB3+YDOtk46xuW7bSpr/p+WUIn6m2tSynmtk+8lQy0XOnxLNgL1ELVC+gk66SywV8=" %}

```
title: DIGIT TM II selection process 

_: **1. Launch  **
EU team -> Consortium: Request
note:
- Profile
- Level range
- Start date
- Number of days
- Delivery mode

_: **2. Consortium selection  **

Consortium <-> Company : Collect CV
Consortium -> EU team : Propose candidates

if: If : at least 1 candidate is suitable
  EU team -> Company : Invite candidate for interview
  Company -> Candidate : Notify Candidate
else: else : no candidate is suitable
  EU team -x Consortium : Reject proposal
  EU team --> Consortium : Request sent to next Consortium
  
  ...: {fas-spinner} 3 business days max per Consortium
  
end

_: **3. Candidate selection **
Candidate -> EU Team : Join interview

If : Candidate not selected
EU team --> Consortium : Request sent to next Consortium
else : Candidate selected
EU team -> Company : Confirm candidate
end

_: **4. Candidate onboarding **

Company -> Candidate : Propose contract
Candidate -> Company : Sign contract
Consortium -> Eu Team : Sign contract
Candidate -> Eu Team :  Join EU Team
 
```

