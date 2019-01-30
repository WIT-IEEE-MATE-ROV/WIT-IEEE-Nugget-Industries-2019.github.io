---
layout: default
---
# Documentation Guidelines
The software documentation for this project is using markdown hosted on Github Pages. You can read about 
all the useful things markdown lets you do [here](https://guides.github.com/features/mastering-markdown/), 
but for now here's an easy overview.

## Step 1: Editing the source to a page
Find the source of the page by looking through the [WIT-IEEE-Nugget-Industries.github.io](https://github.com/WIT-IEEE-Nugget-Industries-2019/WIT-IEEE-Nugget-Industries-2019.github.io)
repository. Once you've found the file you're looking for, click the little pencil icon on the right side
to edit the file. You will then see the source of the file.

## Step 2: Add content
### Adding normal text
Normal text is entered by simply typing. To make a new paragraph, hit enter twice (to make sure that
there's at least one emtpy line seperating the two paragraphs). Hitting enter once will not create a new paragraph.
This is useful because text does not wrap around, so you can hit enter once to keep everything visible without messing up 
your formatting.

### Adding headers
One '#' will create a header, '##' will create a sub-header, '###' will create a sub-sub header, etc:
```
# I am a header
## I am a sub-header
### I am a sub-sub header
```

### Adding code snippets
Surround code with backticks (\`like this\`) to add code snippets in-line. They'll end up looking `like this`. 

For multi-line code snippets, use three backticks. You can also specify the language with the first three backticks:
```
\`\`\`C
int main(void)
{
    return 0;
}
\`\`\`
```

That code looks like this:
```C
int main(void)
{
    return 0;
}
```

## Step 3: Publish the content
Hit 'preview' to preview your page. It should look properly formatted and not be plain text. If it is plain text, make 
sure that your file ends in .md, and has this header at the top:
```
---
layout: default
---
```

If you're satisfied with how it all looks, hit the green 'Commit new file' button. It should take less than 30
seconds to automatically publish your content.




