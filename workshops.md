# Workshop handbook


## Timelines

### For Workshop Organisers

#### Reviewing

Typically between 14-30 days is enough time for reviewing. It is useful to ask some reviewers to be emergency reviewers designated before the review process begins, as there are always reviewers who do not finish their reviews and you will therefore need to do it.

#### Camera Ready

#### Proceedings

#### Uploading videos/papers

#### Proceedings

Softconf vs. Openreview

I have a preferance for softconf, but regardless of choice, make sure to add the workshop chairs as admins of the workshop submission site. This will help if there are any time-sensitive issues.

#### Software

We use [ACLPUB2](https://github.com/rycolab/aclpub2). Using ACLPUB that is built into softconf has been deprecated. While ACLPUB2 is still very new and currently in active development and has some bugs, this is the process that will be used moving forward. Do report bugs as you find them, and ideally, create pull requests for any bugs that you fix.

##### Required items:
- A schedule: Manually defined in `program.yml`
- A list of papers: Automatically generated (from the script fetching data) and stored in `papers.yml`.
- A description of the workshop: Manually defined in `description.yml`.
- A list of organizers: Manually defined  in `organizing_committee.yml`
- A list of prefaces: Manually defined in prefaces.yml

##### Notes
The only date format that is accepted is: `YYYY-MM-DD HH:MM:SS`

###### Schedule: `program.yml`

Should contain:
- Different sessions
- Start/End times of each session
- IF papers are already assigned to a session, include them but if not, simply do not list them.
- IDs need to be in text quotes to match up with the IDs in `papers.yml`.

###### Papers: `papers.yml`
Tasks:
- Manually go over each paper and make sure that no formatting issues (e.g., all characters are displayed correctly).
- IDs need to be in text quotes.
- Unarchived papers should be flagged with 'archived: False'.
  - This includes Findings papers to be presented.

####### Findings Papers
All findings papers presented at the workshop need to be added to `papers.yml` to be included.

Recommendation: As all papers in `papers.yml` need to have an ID, I would recommend giving each finding paper alphanumeric IDs, starting with `F1` to `F[n]`.


###### Description: `description.yml`
Should contain:
- date & start time of the workshop.
- title of the workshop (including Workshop number).
- chair: Name of each chair without affiliation.
- location: Filled in by workshop chairs.
- id: `workshop_<workshop_[number]>` (e.g., `workshop_1`)
- url: Webpage for the workshop
- abstract: A brief description of the workshop (2-3 sentences).

###### Prefaces: `prefaces.yml`
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

##### Automatically populating files

1. Create webservices on softconf for reviewer and submission information (softconf output should be CSV files).
2. Copy the `softconf` directory over to the workshop repository.
3. Edit the config.json files with the appropriate information.
4. Run `softconf2aclpub.py`.

##### Manual steps

1. Populate program.yml.
2. Populate prefaces.yml and create the appropriate tex files.
3. Add the flag `archival: false` to all papers that are non-archival
4. Remove all references to `attachments` where the attachment is `<submission number>.txt`.
5. Add all findings papers to be presented, set the ID to `F<number>`.
6. Ensure all ID numbers in `id` are strings.
7. Verify the contents of all generated files.
8. Check that `organizing_committee.yml' is generated with the organizers' information.
9. Remove 'chairs' from `program_committee.yml`.
10. Check all files for unicode issues (search for `\x`).

##### Compiling the Proceedings

Clone the [ACLPUB2](https://github.com/rycolab/aclpub2) repository and the workshop Github repository into the same root directory. The structure should look like this:

| Root directory
| | aclpub2
| | <workshop repo>

Create a virtual environment for building the proceedings and installing python packages.
Personally, I use virtualenv, so my instructions are for that but use any you like.

Go to the aclpub2 directory (and subdirectories) and install all packages.
Add: `export PYTHONPATH="/path/to/aclpub2"` to your virtual environment definition file (e.g., for virtualenv, the file is `venv_dir/bin/activate`)

Steps:

1. Make sure to be in the workshop directory's root.
2. Run `/path/to/aclpub2/bin/generate . --proceedings --overwrite`
3. ??? (bugfix)
4. Profit.


#### Reviewer Management Guide

- Invite reviewers via softconf
-


#### For Workshop Chairs & Conference Organisers

##### Deadlines

##### ISBN

##### Proceedings

#####
