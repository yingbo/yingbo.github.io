Title: How to lock screen from command line on a Mac
Date: 2014-09-22 18:24
Author: yingbo
Category: Mac
Slug: how-to-lock-screen-from-command-line-on-a-mac
Status: published

Interesting enough, there is no easier way than do a little "programming". I found the following solution on http://apple.stackexchange.com/questions/80058/lock-screen-command-one-liner/123738\#123738:

Creating "main.m" by any text editor:  
<!--more-->

` #import  #import `{lang="objc" no_wrap="false" line_numbers="false"}

int main () {  
NSBundle \*bundle = \[NSBundle bundleWithPath:@"/Applications/Utilities/Keychain Access.app/Contents/Resources/Keychain.menu"\];

Class principalClass = \[bundle principalClass\];

id instance = \[\[principalClass alloc\] init\];

\[instance \_lockScreenMenuHit:NULL\];

return 0;  
}  
</code>

Then compile it with clang (from Xcode):

` clang -framework Foundation main.m -o lock`{lange="bash"}

Then run the "lock" will lock your screen immediately.
