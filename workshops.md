---
layout: workshop
title: Workshop Guide
permalink: /workshops
---

# Table of Contents
* TOC
{:toc}


# For Workshop Organisers

## Submitting Your Proposal

### Notes for All Workshops
#### Diversity

Simply stating that the reviewing pool is diverse is not enough.
When we are talking about diversity, we do not mean diversity between academia and industry.
In particular, focus on diversity in the invited speakers (past and planned) and the organising committee.

If you are only able to show diversity along parameters of academia & industry and seniority, you're a step behind workshops that take the diversity question seriously.

Having said that *do* highlight topics of diversity that are inherent to the topic or focus of the workshop (that year). e.g., A workshop on summarisation that is focusing on summarisation and simplification for people with reading comprehension difficulties should absolutely highlight that the topic of the workshop is intrinsically linked to diversity in the field (back this up by inviting experts to speak on the topic).

#### Unsettled Topics

Some years, there are not a lot of spaces for workshops and it is the smallest things that make the difference. So for that reason, I would recommend *not* describing things that are not settled. For instance, if you are planning a shared task, but do not have a chair to organise the shared task, it would be better simply not to list it. The exception to this rule are speakers and panels: Do note who you have reached out to, whether they have responded or not.

### New Workshops

### Recurring Workshops

When you're at this point you should know how to write a workshop proposal, but here are helpful areas to focus on:

- Were your past workshops a success (how many submissions/accepted papers)?
- Why is the workshop still relevant?
- How is the proposed workshop edition innovating on past editions (e.g., focus, topic, new initiative like a shared task, etc.)
- How have you addressed the issue of diversity in the field before? [See some guidance here.](#note-for-all-workshops:-**Diversity**)
- Is your program committee more or less settled?
- Is your timeline (with any new additions) realistic? How can you make it realistic if it is not?

## Organising Workshops

### Reviewing

Typically between 14-30 days is enough time for reviewing. It is useful to ask some reviewers to be emergency reviewers designated before the review process begins, as there are always reviewers who do not finish their reviews and you will therefore need to do it.

### Reviewer Management Guide

- Invite reviewers via softconf
- E-mail them with reminders to review: Typically 7 days and 3 days before the deadline is enough, though sometimes you also need to remind on the review deadline.

### Camera Ready

It is typically a good idea to give authors ~10 days to address reviews. Decisions are also useful to make on the basis of whether the issues raised in the review can be addressed in that span of time.
After authors have uploaded their camera ready versions, you should check them to make sure that they adhere to the ACL style. If they do not, help the authors address the issues for compliance.

#### Uploading videos/papers to Underline/Conference Platform

The folks who are running the virtual platform will need to know the submission ID for each paper that you accept. This will typically you will be requested the following information in a spreadsheet for each paper:

- [Mandatory] Submission ID: The Softconf/OpenReview submission ID.
- [Mandatory] Title: Title of each papers.
- [Mandatory] Type: Talk/Poster.
- [Optional] Chair: First name, Second name (if different from organizer): Can leave this blank.
- [Mandatory] Do you need a virtual space in GatherTown (Yes/No): If it's a poster and will be presented virtually, the answer is most likely 'Yes'.
- [Mandatory] Requires Zoom link (Yes/No): Default answer is "Yes" for all in-person talks and virtual talks. The Zoom is managed and recorded by the conference provider.
- [Optional] Self-provided zoom link: If you are using your own Zoom link, provide it here.

For the Gathertown and Zoom questions, only one link will be produced for each but *do* answer in all rows, to make sure that all papers are correctly assigned by the virtual conference platform.

#### Uploading videos, posters, and/or slides

The virtual conference provider will set a deadline for uploading the content. This is a hard deadline that *must* be taken into account when planning the workshop schedule.

**Recommendation**

I would recommend that you have every presenter create a poster *and* a video presentation. This is more work for the authors before the conference, but it means that both talks and posters are treated equally after the workshop has concluded.

## Building Proceedings

It is important that workshop organizers know one single thing: Any delay from one workshop delays the proceedings for the main conference and all other workshops. For this particular thing, delays are unacceptable.

### Softconf vs. Openreview

I have a preferance for softconf, but regardless of choice, make sure to add the workshop chairs as admins of the workshop submission site. This will help if there are any time-sensitive issues.

### Software

We use [ACLPUB2](https://github.com/rycolab/aclpub2). Using ACLPUB that is built into softconf has been deprecated. While ACLPUB2 is still very new and currently in active development and has some bugs, this is the process that will be used moving forward. Do report bugs as you find them, and ideally, create pull requests for any bugs that you fix.

### Required items:
- A schedule: Manually defined in `program.yml`
- A list of papers: Automatically generated (from the script fetching data) and stored in `papers.yml`.
- A description of the workshop: Manually defined in `description.yml`.
- A list of organizers: Manually defined  in `organizing_committee.yml`
- A list of prefaces: Manually defined in prefaces.yml

#### Notes
The only date format that is accepted is: `YYYY-MM-DD HH:MM:SS`

##### Schedule: `program.yml`

Should contain:
- Different sessions
- Start/End times of each session
- IF papers are already assigned to a session, include them but if not, simply do not list them.
- IDs need to be in text quotes to match up with the IDs in `papers.yml`.

##### Papers: `papers.yml`
Tasks:
- Manually go over each paper and make sure that no formatting issues (e.g., all characters are displayed correctly).
- IDs need to be in text quotes.
- Unarchived papers should be flagged with 'archived: False'.
  - This includes Findings papers to be presented.

###### Findings Papers
All findings papers presented at the workshop need to be added to `papers.yml` to be included.

Recommendation: As all papers in `papers.yml` need to have an ID, I would recommend giving each finding paper alphanumeric IDs, starting with `F1` to `F[n]`.

#### Description: `description.yml`
Should contain:
- date & start time of the workshop.
- title of the workshop (including Workshop number).
- chair: Name of each chair without affiliation.
- location: Filled in by workshop chairs.
- id: `workshop_<workshop_[number]>` (e.g., `workshop_1`)
- url: Webpage for the workshop
- abstract: A brief description of the workshop (2-3 sentences).

##### Prefaces: `prefaces.yml`
The format of the file is:
```
- title: <Section Heading>
- file: <Path to file>
```

The title will be used as the section heading in the compiled proceedings, so if you would a sectioned titled  "Introduction" that is defined in `introduction.tex` located in the `prefaces/` directory. Your `prefaces.yml` should look like this:

```
- title: "Introduction"
- file: "prefaces/introduction.tex"
```

All files will be included in the proceedings.tex file, so there is no need for begin/end document or a preamble. Simply have the content in the file.

#### Automatically populating files

1. Create webservices on softconf for reviewer and submission information (softconf output should be CSV files).
2. Copy the `softconf` directory over to the workshop repository.
3. Edit the config.json files with the appropriate information.
4. Run `softconf2aclpub.py`.

#### Manual steps

1. Populate program.yml.
2. Populate prefaces.yml and create the appropriate tex files.
3. Add the flag `archival: false` to all papers that are non-archival
4. Remove all references to `attachments` where the attachment is `<submission number>.txt`.
5. Add all findings papers to be presented, set the ID to `F<number>`.
6. Ensure all ID numbers in `id` are strings.
7. Verify the contents of all generated files.
8. Check that `organizing_committee.yml` is generated with the organizers' information.
9. Remove 'chairs' from `program_committee.yml`.
10. Check all files for unicode issues (search for `\x`).
11. Fill in the `description.yml` file.

#### Compiling the Proceedings

Clone the [ACLPUB2](https://github.com/rycolab/aclpub2) repository and the workshop Github repository into the same root directory. The structure should look like this:

```bash
├── root_folder (e.g., ~/Documents)
| ├── aclpub2
| ├── workshop_repo
```

Create a virtual environment for building the proceedings and installing python packages.
Personally, I use virtualenv, so my instructions are for that but use any you like.

Go to the aclpub2 directory (and subdirectories) and install all packages.
Add: `export PYTHONPATH="/path/to/aclpub2"` to your virtual environment definition file (e.g., for virtualenv, the file is `venv_dir/bin/activate`)

Steps:

1. Make sure to be in the workshop directory's root.
2. Run `/path/to/aclpub2/bin/generate . --proceedings --overwrite`
3. ??? (bugfix)
4. Profit.

## For Workshop Chairs and Conference Organisers

The very first bit of advice that I can offer is: Create a google group for all communication with workshop chairs. It streamlines information a lot and it makes it a lot easier. I *cannot* recommend this enough.

### Deadlines

There are some deadlines that are soft and others are hard. It is usually helpful to workshop organizers if the proceedings & video upload deadlines are pushed back, since these are often what influences submission and camera ready deadlines.

- Proceedings deadline: There's a whole project here with getting
- Paper & Video upload (e.g. on Underline)
- Submitted papers deadline

### ISBN

The information needed to generate ISBNs is incredibly simple: The title of the proceedings for each workshop. This can be obtained quite early on, so that once main conference proceedings ISBNs are ready to be requested, the workshop ones can be ready. I would suggest creating a spreadsheet

### Proceedings

Developing the proceedings and dealing with workshops can be a time-consuming and error prone task. Make sure to suggest that workshop chairs dedicate time *at least* 1 week in advanced of submission. This also means that the camera ready deadline needs to be at least 8 days before the proceedings deadline.
Proceedings cannot be generated until workshop chairs create the github repositories, so create these early and give access to all workshop chairs.

