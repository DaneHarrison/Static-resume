<div align="center">
<h1>Publishing your resume to GitHub Pages</h1>

</div>

Having recently read through *Modern Technical Writing by Andrew Etter*, I wanted to share my new understanding of documentation and some of the tools available. Since the best way to learn is through *practical application*, we will be using VSCode, Hugo and Markdown to transform then host your resume onto GitHub pages. 

Documentation is the secret to long term knowledge and easier collaboration, however, as software changes over time, so must its documentation. This can become a problem with convential methods. Enter static sites. Static sites are simple, portable, secure, easy to modify and distribute as changes are made. Furthermore, as projects scale static site generators like Hugo can address their growing complexity by offering a more modular, automatable and customizable process. 

<br>

These notes have careful consideration to the Etters suggested practices: 
- Basic Functional Documentation
- Explorative nature of documentation
- Careful consideration to everyone's time
- The role of modern technologies
- Making content beautiful, discoverable, scannable, and searchable

If you wish to contribute, all suggestion are welcome by [pull request](https://github.com/DaneHarrison/daneharrison.github.io/pulls).




<br>

## Requirements
- Knowledge of basic command line manipulation
- Knowledge and access to VSCode
- Knowledge of markdown
- Access to Git
- A GitHub account
- A resume

<br>

## Overview
[Setting up your environment](#setting-up-your-environment)
- [Creating your GitHub repository](#creating-your-github-repository)
- [Connecting VSCode to your GitHub](#connecting-vscode-to-your-github)
- [Configuring Hugo](#configuring-hugo)

[Creating your new resume](#creating-your-new-resume)
- [Hugo setup script](#hugo-setup-script)
- [Loading the Hugo-Resume theme](#loading-the-hugo-resume-theme)
- [Making changes](#making-changes)

[Deployment](#deployment)
- [Finishing touches](#finishing-touches)
- [Commiting changes](#commiting-changes)
- [GitHub Actions](#github-actions)

[Results](#results)

<br>

[Appendix](#appendix)
- [Authors and acknowledgments](#authors-and-acknowledgments)
- [More Resources](#more-resources)
- [FAQs](#faqs)


<br>
<br>

# Instructions:
## Setting up your environment
<br>

### Creating your GitHub repository
1. Navigate to the repositories tab on your GitHub account to click on "New" near the top right of the page

2. Name it **GitHubName**.github.io, note that **GitHubName** should be replaced by whatever yours may be

3. Select the public visibility option

4. Scroll to the end of the page to click "Create Repository"

### Connecting VSCode to your GitHub
5. Copy the HTTPS link provided in the blue Quick Setup box after your GitHub repository was created

6. Transition to VSCode

7. Open a new terminal

7. Navigate to a directory to store your code

8. Type into the command line the following: git clone **link**, note that **link** should be replaced by the content we copied in *step 5*

### Configuring Hugo
10. Naviage [here](https://go.dev/doc/install), although we will not need this resource, by clicking on download, the name of the file tells informs us of our computer's architecture

11. Navigate [here](https://github.com/gohugoio/hugo/releases) to find the most recent release of Hugo under *assets*. The release we want will match your computer's operating system and architecture, which we discovered in step 9

12. Extract the downloaded content to the location of your choice 

13. Copy the path of the downloaded content

14. Search up environment variables on your computer

15. Add this path to your environment variables

16. Close out and reopen VSCode and all active terminals

17. Confirm hugo now works on your computer by entering the following into any command line: hugo version

<br>
<br>

## Creating your new resume
<br>

### Hugo setup script
18. Transition to VSCode

19. Open up your project folder and location in the VSCode command line interface

20. Run the command: hugo new site **name**, where **name represents the name you would like to give the resumes static site**.

### Loading the Hugo-Resume theme
21. Navigate to the themes folder in VSCodes command line

22. Run the command: git clone url https://github.com/OGGampy/hugo-resume

23. Create a new file at the top level of the project folder called .gitmodules

24. Paste the following code snippet inside of the newly created .gitmodules :     
   
```  
   [submodule "path_to_submodule"] 
       path = themes/hugo-resume
       url = https://github.com/OGGampy/hugo-resume
```
### Making changes
25. Convert your resume into markdown

26. Copy the entire contents folder from the theme and paste into your own projects

27. Check that the themes folder is collapsed to prevent confusion between the themes files and your resumes

28. Modify the projects config.toml, note that changes required beyond pasting the contents below will be marked by ***:
```
title = "***your name here"
theme = "hugo-resume"
baseURL = ""
languageCode = "en-us"
PygmentsCodeFences = false
PygmentsCodeFencesGuessSyntax = true
PygmentsStyle = "monokai"
enableGitInfo = false

[params]
address = "***Winnipeg, MB"
email = "***"
favicon = ""
firstName = "***Dane"
lastName = "***Wanke"
phone = ""
profileImage = ""
showEducation = false
showExperience = true
showOpenSource = false
showProjects = true
showPublications = false
showQr = false
showSkills = false

[params.google]

[params.google.analytics]
trackerID = ""

[[params.handles]]
link = "***https://www.linkedin.com/in/dane-wanke-b22b44250/"
name = "LinkedIn"

[[params.handles]]
link = "***https://github.com/DaneHarrison"
name = "GitHub"

[outputs]
home = ["HTML", "JSON"]

[taxonomies]
tag = "tags"
```
29. Add experience.json into data 

30. Format the content by the following:
```
[
    {
        "role": "your role",
        "company": "the company",
        "summary": "the summary with \n\n to distinguish new lines",
        "range": "range of time you worked there for"
    },
    ... for all experiences you would like to include
]

```
31. Edit the project folders _index.md to contain your personal information from your resume

32. Delete all the files in the contribution folder except _index.md

33. Modify the content in the creations folder so there is a markdown file for every project you plan to add in addition to _index.md

34. Rename these markdowns according to the projects they will represent

35. Add photos you plan to use to showcase these projects into the static folder at the top of the projects folder

36. Return to the creation mark down files and modify them as follows:
```
{
    "title": "your projects name",
    "featured": true,

    "description": "A description of your project.",

    "image": "the name of the file you added in step 35 or blank if not applicable",
    "link": "a link to your project",
    "tags": ["meaningful", "tags"]
}


Copy paste the same description given above.
```
37. Run the command: hugo server

38. Verify your resume is functional and has the information you intended

<br>
<br>

## Deployment
<br>

### Finishing touches
39. Double check your personal information note that it will be difficult to remove from GitHub once posted

40. Change the base URL inside of config.toml to your GitHub repositories link. Note that this change will need to be reverted to work on hugo's development server which we ran in step 38

### Commiting changes
41. Commit your changes with an accurate message

42. Push to your repository

### GitHub Actions
43. Go to GitHub settings and ensure GitHub Pages is active

44. Scroll down and select the GitHub Actions deployment of GitHub Pages

45. Select the boilerplate Hugo script

46. Commit this script to your repository

47. Go to the Actions tab

48. Click on the name of the script we created which should be displayed in a menu on the left hand side 

49. Click on run workflow in the blue box that appeared after step 48

<br>
<br>

## Results


<br>
<br>
<br>

# Appendix

## Authors and Acknowledgments
Andrew Etter was a great inspiration for me creating this tutorial which heavily relied on the work Eddie Webbinaro put into his Hugo-Resume theme. I also wanted to thank Frieda Bi, Hamdi Elzard and Dirk Page for reviewing and providing their feedback.


<br>

## More Resources
- [VSCode tutorial](https://code.visualstudio.com/docs)
- [Command line tutorial](https://www.freecodecamp.org/news/command-line-for-beginners/)
- [Markdown tutorial](https://www.markdowntutorial.com/)
- [Hugo documentation](https://gohugo.io/documentation/)
- [Hugo themes](https://themes.gohugo.io/)
- [What is a pull request?](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
- [Technical Writting by Andrew Etter](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS)
- [Eddie Webbinaro's GitHub](https://github.com/eddiewebb)

<br>

## FAQs
### 1. Why is Markdown better than a word processor?

PDFs, the most popular export format from word documents, do not work well with version control. Version control is a necessity that allows easier modification and distribution of product documentation. Therefore, it makes more sense to use Markdown which is simple to use, well supported and integrates web technologies like HTML and CSS for further customizability.

<br>

### 2. Why is my resume not showing up?

Sometimes using GitHub Actions and GitHub Pages can take a while. If this is the case, you can always check the status of the deployment under the Actions tab. If there are any issues clicking on the status symbol (either the red X, pulsing yellow circle or green check) will display more information enabling you to address potential issues.

<br>

### 3. Does my GitHub repository need to use this particular naming convention?

**Yes**, a repository that is set to **GitHubName**.github.io, note that **GitHubName** should be replaced by whatever yours may be, automatically enables GitHub pages. Although more importantly, the theme we use modifies the sites URL. Therefore, using anything else potentially break links within your resume.