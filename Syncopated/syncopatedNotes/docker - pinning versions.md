---
---


It makes sense to do this, but in practice, sometimes it turns out to be a waste of time. This week I attempted to revive two projects that haven't been updated in ~2 years. Both projects presented headaches in the form of versioned packages that were no longer available. 

I suppose I would argue it would take just as much effort to maintain a project that conforms to package updates. Instead of marking `package==0.25.2` just mark `package` and if there is an update to the package that "breaks the code", then update the code. Because some years later when package 0.25.2 is no longer easily available on a active mirror, then whomever picks up the project has the task of resolving dependencies for code they didn't write. There are too many libraries and too many versions to keep track of long term. The reliance on the various package managers like conda or pyenv or...or rbenv or rvm (or recently asdf) is making the tasks of deployment and maintenance rather tedious. 