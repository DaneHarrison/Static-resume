<div align="center">
<h1>Publishing your resume to GitHub Pages</h1>

</div>

Having recently read through *Modern Technical Writing by Andrew Etter*, I wanted to share my new understanding of documentation and some of the tools available. Since the best way to learn is through *practical application*, we will be using VSCode, Hugo and Markdown to transform then host your resume onto GitHub pages. 

Documentation is the secret to long term knowledge and easier collaboration, however, as software changes over time, so must its documentation. This can become a problem with more traditional methods. Enter static sites. Static sites are simple, portable, secure, easy to modify and distribute as changes are made. Furthermore, as projects scale static site generators like Hugo can address their growing complexity by offering a more modular, automatable and customizable process. 

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
- Knowledge of Markdown
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
1. Create a new repository from the respoistories tab on your GitHub account

2. Name it **GitHubName**.github.io, note that **GitHubName** should be replaced by whatever yours may be

3. Select the public visibility option

4. Click "Create Repository"

### Connecting VSCode to your GitHub
5. Copy the HTTPS link provided in the blue Quick Setup box after your repository is created

6. Open VSCode

7. Open a new terminal

8. Navigate to a directory to store your code

9. Type the following into the command line: git clone **link**, note that **link** should be replaced by the content we copied in *step 5*

### Configuring Hugo
10. Naviage [here](https://go.dev/doc/install), although we will not need this resource, by clicking on download, the name of the file tells us about our computer's architecture

11. Navigate [here](https://github.com/gohugoio/hugo/releases) to find the most recent release of Hugo under *assets*. The release we choose will match your computer's operating system and architecture, which we discovered in *step 10*

12. Copy the path of wherever the downloaded and extracted content is on your system

13. Search up environment variables on your computer

14. Add the path we copies in *step 12* to your environment variables

![setting the environment variable](gifs/settingVars.gif)

15. Close and reopen VSCode and all active terminals

16. Confirm hugo now works on your system by entering the following into any command line: hugo version

<br>
<br>

## Creating your new resume
<br>

### Hugo setup script
17. Open up your project folder in VSCode and its command line

18. Run the command: hugo new site **name**, where **name** will later be given to the static site we are creating.

### Loading the Hugo-Resume theme
19. Navigate to the themes folder in VSCodes command line

20. Run the command: git clone https://github.com/OGGampy/hugo-resume

21. Create a new file at the top level of the project folder called .gitmodules

22. Paste the following code snippet inside of the newly created .gitmodules:     
   
```  
   [submodule "path_to_submodule"] 
       path = themes/hugo-resume
       url = https://github.com/OGGampy/hugo-resume
```
### Making changes
23. Convert your resume into Markdown

24. Copy the theme's content folder and paste it in your own. Do not forget to collapse the theme folder affterwards to prevent potential mixup

![copying the themes content folder into your own](gifs/copyingContent.gif)

25. Modify the projects config.toml, note that changes required beyond pasting the contents below will be marked by ***:
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
26. Add experience.json into the data folder 

27. Format the content as follows:
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
28. Edit the project folders _index.md to contain your personal information from your Markdown resume

29. Delete all the files in the contribution folder **except _index.md**

30. Adjust and rename the Markdown files in the creations folder so there is a Markdown file for every project you plan to add **in addition to _index.md**

31. Modify the Markdown files from *steps 30* as follows:
```
{
    "title": "your projects name",
    "featured": true,

    "description": "A description of your project.",

    "image": "the name of the file you added in step 35",
    "link": "a link to your project",
    "tags": ["meaningful", "tags"]
}


Copy paste the same description given above.
```
![an example of what these modifications look like](gifs/finshedChanges.gif)

32. Run the command: hugo server

<br>
<br>

## Deployment
<br>

### Finishing touches
33. Verify your information, note confidential information may be difficult to remove from GitHub once posted

34. Change baseURL inside of config.toml to your GitHub repositories link. Note that this change will needs to be reverted to rerun hugo's development server we used in *step 32*

### Commiting changes
35. Commit your changes with an accurate message

36. Push to your repository

### GitHub Actions
37. Scroll down and select the GitHub Actions deployment method of GitHub Pages

38. Select and commit the boilerplate Hugo script to your repository

![navigating through the options from Actions](gifs/actionsWalkthough.gif)

39. Navigate to the Actions tab

40. Click on the script we created in *step 38* displayed on the left hand side 

41. Click on run workflow in the blue box

<br>
<br>

## Results
### https://daneharrison.github.io/
![How to initially access your resume](gifs/finalProduct.gif)
<br>
<br>
<br>

# Appendix

## Authors and Acknowledgments
Andrew Etter was my inspiration for creating this tutorial which relied upon Eddie Webbinaro's Hugo-Resume theme. I also wanted to thank Frieda Bi, Hamdi Elzard and Dirk Page for their time and feedback.


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

PDFs, the most popular export format from word documents, do not work well with version control. Version control is a necessity that allows easier modification and distribution of product documentation. Therefore, it makes more sense to use Markdown which is simple to use, well supported and integrates web technologies like HTML and CSS for familiar customizability.

<br>

### 2. Does my GitHub repository need to use this particular naming convention?

For this tutorial yes, a repository that is set to **GitHubName**.github.io automatically enables GitHub pages. Although more importantly, the theme used in this tutorial modifies the sites URL. Therefore, using anything else may break links within your resume.