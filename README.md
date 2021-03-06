
# Migrate pages from Wiki extension to new VSTS Wiki

## Migration Summary
Migration of markdown pages from Wiki extension to VSTS wiki is a simple 4 step process:
1.	Clone the VSTS Wiki 
2.	Move & commit all markdown pages to VSTS Wiki
3.	Run the migration tool provided by Microsoft (link)
4.	Push the changes to the master branch on VSTS Wiki

## Detailed steps
Here are the detailed steps for Wiki migration:

1.	Go to **Wiki*** hub in VSTS.  Create your first Wiki page (You can create a dummy page and always delete it later)
 
2.	Click on **More** -> **Clone Wiki** -> and clone your VSTS Wiki repo using **git clone** command.

<img src="https://github.com/sandeepchads/vsts-wikiTools/blob/master/Images/1%20Clone%20wiki.PNG">

Let the clone location be "LocationA" with respect to the document. E.g with respect to this document "C:\Users\sancha\WikiDemo.wiki"

<img src="https://github.com/sandeepchads/vsts-wikiTools/blob/master/Images/2%20Git%20Clone.PNG">
 
3.	Clone the Wiki extension repo. The Wiki will be mapped to a folder given by you during the wiki creation. You can check that by going to "manage wiki" option in the existing wiki as shown below.

<img src="https://github.com/sandeepchads/vsts-wikiTools/blob/master/Images/3%20Wiki%20extension.PNG">

The value under the label "Root" is the folder in your repo inside which the existing wiki pages are saved.

4.	Say you have cloned the above mentioned "sampleWiki" in the location "C:\wiki\sampleWiki". The wiki pages will be saved in the path "C:\wiki\sampleWiki\ _extensionWiki". Let this be "LocationB" with respect to the document.
 
5.	Create an empty folder in any path of choice in your location machine and let that be "LocationC" with respect to the document.
 
> Just to summarize 
- Location A = VSTS Wiki 
- Location B = Wiki extension 
- Location C = Empty folder where we will run our migration tool

6.	Open command prompt as an administrator

7.	Run **MigrateToVSTSWiki.exe** as shown below to copy the files from your existing wiki and copying them to the destination directory provided. During copying, the exe converts the pages to be compliant with VSTS wiki.
 
**Format:** MigrateToVSTSWiki.exe /source:LocationB /destination:LocationC

E.g. In the example above:
- "E:\wiki\sampleWiki\_extensionWiki" is the folder in which the existing wiki files are present.
-	"E:\Temp\Wiki\New" is the empty folder into which the migrates files will get dropped.

<img src = "https://github.com/sandeepchads/vsts-wikiTools/blob/master/Images/4%20Migate%20to%20VSTS%20Exe.PNG">

8. Now remove all files from the path "LocationA" (if any) apart from the git related files such as .gitignore etc.

9. Copy all the files from the path "LocationC" and paste them into "LocationA"
 
10.	Run **git add .** to stage all the newly added files in the  "LocationA" for commit.
  
11.	Run **git commit -m <commit message>** to commit the files that you have staged locally.
  
<img src = "https://github.com/sandeepchads/vsts-wikiTools/blob/master/Images/5%20Git%20commit.PNG">  

12.	Run **git push origin wikiMaster -f** .Push the changes on to the default branch of the VSTS Wiki.

## Source code
Repository for the documentation - https://github.com/Microsoft/vsts-wikiTools


## Feedback
For bugs, questions and discussions please use the [GitHub Issues](https://github.com/Microsoft/vsts-wikiTools/issues).

Want to learn more about the new and exciting features of VSTS Wiki. Visit [this blog post - coming soon](comingsoon) for more details.

## Contributing
This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
