# CS 255 Portfolio: DriverPass

This repo has my Business Requirements Document (Project One) and my System Design Document (Project Two) for the DriverPass project.

## Summarize the DriverPass project

DriverPass was the client. They're a company that helps students pass their DMV driving test. Liam, the owner, and Ian, the IT officer, wanted a web-based system where customers can book, change, or cancel 2-hour driving lessons online and take online practice tests. Each lesson gets matched with a driver and a car. The system also needed different roles (customer, secretary, driver, owner, and IT officer), a record of who made every change, reports that can be downloaded to Excel, and updates from the DMV so the practice tests stay current. The system runs in the cloud so DriverPass doesn't have to handle its own servers and backups.

## What did I do particularly well?

I think I did best at tying my design back to what the client actually said in the interview. Almost every piece of the design points to something Liam or Ian asked for. Liam wanted to know who made each booking, so I put an activity log step in the Make Reservation activity diagram and the sequence diagram. Ian didn't want to get calls about forgotten passwords, so I made a Reset Forgotten Password activity diagram where customers use a one-time email link. In that one I also made the system show the same message whether or not the email has an account, so nobody can guess who's a customer.

I'm also happy with how my diagrams work together. The use case diagram shows who does what (with include and extend for things like choosing a package and DMV updates), the activity and sequence diagrams show how a reservation really works, and the class diagram shows the data behind it. I also explained each diagram in plain bullets so a non-technical client like Liam could follow it.

## What part would I revise?

If I could pick one thing, I'd revise the PaymentInfo class in my class diagram. Right now it stores the card number, expiration date, and security code, with the number and code marked as encrypted. That doesn't match my own Technical Requirements, where I said a payment processor would handle card details so they aren't stored in plain text. It's also not a good idea to store a card's security code at all, even encrypted. I'd fix it by taking the security code out of the class and having the system keep only a token from the payment processor and maybe the last four digits. Then the class diagram, the technical requirements, and the security slide in my client presentation would all say the same thing.

## How did I interpret the user's needs and put them into the design?

I read the interview and pulled out what each person needed to do, and then turned that into use cases. For example, Liam needed to turn off a package without losing its history, so Package has an isActive flag and the Owner has a Disable a Package use case. Ian needed to cut off someone who leaves the company, so the IT officer can reset or block any account. Customers needed to see which practice tests they passed, failed, or hadn't started, so I added a TestAttempt class with a status. I also kept the limits in mind, like only allowing changes while online so there aren't two copies of the same data, and I told the client about those limits in the presentation instead of hiding them.

Considering the user's needs matters because the system is only useful if the people using it can actually do their jobs with it. If I had designed what I thought was cool, Liam might not get his activity report and Ian would be stuck resetting passwords all day. Finding a missed need on paper is way cheaper than finding it after the system is built.

## How do I approach designing software?

I like to start with the people who will use the system and what they said they need before I think about code. In this project I went from the interview to requirements, then to use cases, then to activity and sequence diagrams, and then to the class diagram and technical requirements. Each step built on the one before it, which made it easier to catch mistakes. For future projects I'd keep that and add a few things:

- **Checking my diagrams against each other** before I turn anything in, since I missed the PaymentInfo mismatch until I looked back.
- **Asking the client follow-up questions early**, especially around security and what happens when things go wrong, like a cancellation or a driver calling in sick.
- **Making wireframes or a quick prototype** so users can react to something visual.
- **Working in small steps and getting feedback often**, like in Agile, instead of waiting until the end.
