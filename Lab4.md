# Use Case Design: Maintain Timecard
## Description of Interaction Between Design Objects
### Identifying Participating Objects
- TimecardForm: A user interface that allows employees to interact with Timecards.
- TimecardController: Coordinates and processes requests.
- Timecard: Represents a managed object within the system.
- Employee: Represents an employee managed within the system.
- ProjectManagementDatabase subsystem: An existing database containing information about projects and charge numbers.
- ProjectManagementDatabase interface: The interface of the ProjectManagementDatabase subsystem.

### Classes and their attributes and methds
##### Timecard
![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XUNSqvYSR52I6PkQd9YKOf2DPU2Wgv2HdvfKN5uVb5sQWgONv1O6P1Qb0dcAIWK9vQbQcY2cUcf9J2jddbf-L3HqeAKn99Kc0HGi9QBoo4rBmLe8G000F__0m00)
##### Employee
![Diagram](https://www.planttext.com/api/plantuml/png/L90z3i8m38Ntd28Z3DoXK35q05M22xY9eH5nKYNE425Eni2Hk08b51Ksl-yz_yZF-wEA384JMI5g2p7ABGtMPqHv5LAkf0F2Kk346rra1-xIk9Cl8dfbm1vGfM0uxnDr68e1MWUCiTH3xnt-U4XWxCU1JEXuXzpxztGfJMmXQyYBPP5dv56loIV7VsXkc_5ckcmcTGfX31uDeOBmZIgmAbbWRCkUcn0LEZr-uWK00F__0m00)
##### TimecardController
![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XSGEESa5XShX6JcfYOd5gKuv-UL5ENdvAGMALHpAG11Ucg9SsbHKMfU2Ko9XYPS8YEnA3tLEJybjHWgM5gGabYIYgQoEB4CMQWMPAj3QbuAq0400000__y30000)
##### TimecardForm
![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XSNbtDEOd6nGaXcRcfoOb6AMtvHha8rbm8Gf6GM5-GaLi9aD3J1ela5gNbGPcfUIMgHHtvfKJ5GbtD6Ob5wgbzfRb9gKJ5KGMvYPbu94ACPKPnObeeaL0jq19T3QbuAq3q00000__y30000)
##### ProjectManagementDatabaseInterface
![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XSGPEQLf1Qb9IQdAWGKvMUb9fVu9kObfgVcfkQLk2IM92Ob5gSgL7Cf045wQebpHc9HUgfpVafgiOOcLorGkqDgNWhG9000003__mC0)

### Classes Diagram
![Diagram](https://www.planttext.com/api/plantuml/png/X9DBJiCm48RtEOMNiCWT2W545qMHG68zZQU9gH_Hs0P5Y9Enu4XS0SU9cmHQkeZaUVdxyq_o_VcriWx8UIMph91WBRjLhJGT8dlF6CkP1eNnW6D-pMEu1RrVwvs9WJML0Fc8bIVXkWUljaYn09mJMXlFRMCqpcgeGCYX0fr2xJRe6jFVpfYm9NGSkelB6DReGdobZDTkaPh6flJrg6pA59ueD3u9XHLGQgr0Lbw2mp9oFf81gMqqe36UxBEXFV8ajaGIE0Yry8eJA8tEyBxb0J53_-4KHZioKY95uZ-A-q83L6DXEDfJW2HhmLmYxmof4SQ5RILql-PDYtey1Xb8zxq9OMh03qjC0i8QjGlFEGcPw6_QGOMi9FE2bTk0XXhx7Tw0WorOd3cmUD4mVLXBJg9kN9uVCN3Mb1y-vEo8qUVA2N5IQBQmCkVcJHzNbArGy_1x_G000F__0m00)

### Interactions Diagram
![Diagram](https://www.planttext.com/api/plantuml/png/l5L1JiCm4Bpx5LPFSE03HKALMX0SYf3W0zja5OnYErflAkLj77WINy0XJMlIn34SE4IAPktPcV76-Np_M3a6ubgNGh3Y4kKMb67_o1UbCGFAvODX9CXOMUFaHa51e8NmW2LvgwlIDeYYyYmgKnKObelhVk-T9RsOgAsjOR9bYJIrOeZtpORuSxrpZMFKyedi6sQy1GC5QZIy0OOTEB-bqtksuDk8sWFZoOlet-JLpT3CKkf3G3rySHbm3AsB0V2JCOXWAGlaTKtaDSqmXy69KRZhSemhWViKROxpy8oI4QU7x7BbgXAQGCHaSgCD_nJgAr21QvkZ6-yNkeZ4cJ9byOP9Svgsh9LqLerrFn_y8E1eCL7tx814FofixvXxMvFpG6VXiTOxfDP4-d7NLUu5nCShyRYFbr0QwqG02Rb41ZqQcOFzZAQE93szUSRVPzTo_cDYGUbqdQ_GvFuFzmK00F__0m00)

## Simplify sequence diagram using subsystem
![Diagram](https://www.planttext.com/api/plantuml/png/l9L1ReCm44NtFeMLLRle1LAfYaHQDOjKNVG24poYhh2DnaEadAsB7gbNg14X40J6xQ8B9FHj_lnvZE7xyslZ6OXhKmh1cakKUz2MmoNVjC4SICcTPIJ8MJlhvLP3GM24288Z-MYgqfqGHHLSTAuhi2nNzzspJuxCQcOjSvR9bINIt8wntXKRwxjNSX-Oynui56ZGyXOO3k33pYQdFW9Z7rLqT_BkOPnrBSsv_qw-kHruZ3iJ8-7QST3XMXR8MKqKmYqu3xc8IRcjSg6HuDsJKxWiBoIPwFJCJcbVbN0QX9WbDrdmJr3VWGhCd48_NM_OHGHdP8ZYTMBJTzLbyiQfvD6PnUQ4FhkQV13Qe2-rEI0rKTDfrfKA0U9lBv7cvGYdkSu0IE0IcQCeCW_7XKojIJgzPSVVisiy_v7OOAd_McxGgl1_-0400F__0m00)

## Define persistence-related behavior
### Analysis class to Architectural mechanism map from use-case analysis
| Analysis Class     | Analysis Mechanism(s) |
|--------------------|-----------------------|
| Timecard           | Persistency, Security |
| Employee           | Persistency, Security |
| TimecardController | Distribution          |

## Refine the flow of events description
![Diagram](https://www.planttext.com/api/plantuml/png/l5L1JiCm4Bpx5QjSW0CVA1Agr8BeeHK7ZbosyJOOnNPaRmfv6mUUn1Tmr8OcKUe43XmYHRFsxCnuutnzVCuze-DIvqAmufnWZSfmUE19QKhHILWP9eSfAsiyB1Lc3hKG0R0ExdIHsuf85855fQf0mv3SD7llhTF9cTh26dOspycTMz77csPzVFNex2kbl4Q36Maol4J6BVgmijQfziXqaYgQDxY-xMkTWJxwR-3BgnP7tvde0Lt6biCPPCIBqhaWReIvdOimDjHosdNipo3Pq1jOGv0w2hibg1qeVZRIaZSN3FIkF4D5d8X1ueFE5k6WkfQuK_IInk51Az6eZk5BvOiSgs4DtUW76_xfL5xGPRImalnmlxQBI9gHAOptYOrln-NaXKFAeqDFzIV-O4ld0t0GkYdrbbmjTNgQPI63WFZfJKppvmwOndecW0cvHEOe6fd7_OYc0ydqzCOPVvzTpVcFYRLAf-jMY3aP6Nuntm000F__0m00)

## Unify classes and subsystems
![Diagram](https://www.planttext.com/api/plantuml/png/X9DBJiCm48RtEOMNiCWT2W545qMHG68zZQU9gH_Hs0P5Y9Enu4XS0SU9cmHQkeZaUVdxyq_o_VcriWx8UIMph91WBRjLhJGT8dlF6CkP1eNnW6D-pMEu1RrVwvs9WJML0Fc8bIVXkWUljaYn09mJMXlFRMCqpcgeGCYX0fr2xJRe6jFVpfYm9NGSkelB6DReGdobZDTkaPh6flJrg6pA59ueD3u9XHLGQgr0Lbw2mp9oFf81gMqqe36UxBEXFV8ajaGIE0Yry8eJA8tEyBxb0J53_-4KHZioKY95uZ-A-q83L6DXEDfJW2HhmLmYxmof4SQ5RILql-PDYtey1Xb8zxq9OMh03qjC0i8QjGlFEGcPw6_QGOMi9FE2bTk0XXhx7Tw0WorOd3cmUD4mVLXBJg9kN9uVCN3Mb1y-vEo8qUVA2N5IQBQmCkVcJHzNbArGy_1x_G000F__0m00)

