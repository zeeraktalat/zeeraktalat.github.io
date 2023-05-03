# Workshop handbook


## Timelines

### For Workshop Organisers

#### Reviewing

#### Camera Ready

#### Proceedings

#### Uploading videos/papers

#### Proceedings

Softconf vs. Openreview

I have a preferance for softconf, but regardless of choice, make sure to add the workshop chairs as admins of the workshop submission site. This will help if there are any time-sensitive issues.

#### Software

We use [ACLPUB2](https://github.com/rycolab/aclpub2). Using ACLPUB that is built into softconf has been deprecated. While ACLPUB2 is still very new and currently in active development and has some bugs, this is the process that will be used moving forward. Do report bugs as you find them, and ideally, create pull requests for any bugs that you fix.

##### Required items:
- A schedule: Manually defined in program.yml
- A list of papers: Automatically generated (from the script fetching data) and stored in papers.yml.
- A description of the workshop: Manually defined in description.yml.

##### Notes
The only date format that is accepted is: YYYY-MM-DD HH:MM:SS
This is the format and no other.

###### Schedule: program.yml

Should contain:
- Different sessions
- Start/End times of each session
- IF papers are already assigned to a session, include them but if not, simply do not include them.
-
- IDs need to be in text quotes

###### Papers: papers.yml
Tasks:
- Manually go over each paper and make sure that no formatting issues (e.g., all characters are displayed correctly).
- IDs need to be in text quotes
- Unarchived papers should be flagged with 'archived: False'


###### Description: description.yml
Should contain:
- date & start time of the workshop.
- title of the workshop (including Workshop number).
- chair: Name of each chair without affiliation.
- location: Filled in by workshop chairs.
- id: workshop\_<workshop\_ number> (e.g., workshop\_1)
- url: Webpage for the workshop
- abstract: A brief description of the workshop (2-3 sentences).

#### Reviewer Management Guide


#### For Workshop Chairs & Conference Organisers

##### Deadlines

##### ISBN

##### Proceedings

#####
