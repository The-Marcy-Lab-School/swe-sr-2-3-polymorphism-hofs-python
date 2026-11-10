# Explaining Polymorphism and Functions as Values

Say what a caller gains by not knowing a type, and judge when a contract needs enforcing.

- [AI Use on This Assignment](#ai-use-on-this-assignment)
- [Setup](#setup)
- [Instructions](#instructions)
- [Submitting](#submitting)

## AI Use on This Assignment

These are your own words. Do not use AI to draft or rewrite your responses —
that holds in every mode, including implementer mode. You may use it to check
grammar and spelling on writing you have already done, and you may use it
before you start to quiz you until you can explain these ideas without notes.
Paste this if you want that kind of help:

> You are acting as a tutor. Quiz me on what a caller gains by not knowing
> which type it is holding, on what a contract is and where it is written down,
> and on the difference between passing a function and passing the result of
> calling it, until I can explain all of it without looking anything up. Tell
> me when my reasoning is wrong or imprecise. Do not write or rewrite any part
> of my response for me.

A response you did not write is worth nothing to you in an interview, which is
where this writing is really aimed.

## Setup

Clone this repo into `development/mod-2` and `cd` into it. Make a draft branch
before you start.

```sh
git clone [your_repo]
cd [your_repo]
git checkout -b draft
```

There is no code to run here. Pushing tells GitHub to check whether you have
written a response yet, which you can see in the **Actions** tab. That check
counts words. Your instructor reads what you wrote and replies on your pull
request.

## Instructions

Write your response in `short_response.md`. Aim for a response with these
qualities. Your instructor will give you feedback on each one:

- [ ] Addresses all parts of the prompt
- [ ] Accurately uses relevant technical terminology
- [ ] Is free of grammar and spelling mistakes (double check with Grammarly!)
- [ ] Uses markdown to enhance readability (preview in VS Code with
      Command/Control + Shift + V)
- [ ] Is easy to comprehend

## Submitting

```sh
git add -A
git commit -m "your message"
git push
```

Then open a pull request to your instructor for feedback.
