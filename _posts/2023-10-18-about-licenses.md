# About Licenses

**Being open** is a key tenet of the OpenVoiceOS project - so integral that it's part of our name. 
In order to achieve that goal, we have to make sure that our ideology extends to every aspect of the project. 
It is not enough simply to have our code available for people to see; the accompanying license, which defines how that code can be used, must carry this same message. 

In this post, I'll dive into why we chose the licenses we did, and how that affects the ways our code can be used.

## Why do we need a license

First, a quick overview for those not familiar with open source licenses: 
When creating software, it's a good idea to include a specific license. 
This lays out permissions and restrictions over what people using or extending the project can do. 

Without a license, the "defaults" of copyright law apply - usually 'all rights reserved', but it also depends on your country's laws. 
As such, and especially if you want others to extend your code, it's best to release with terms, even if the point is to be *more* permissive than the law presumes. 
Different licenses delineate rights and permissions differently, and there are a [wide variety of prewritten open source licenses](https://opensource.org/licenses/) to choose from.

## Favorite Licenses

Some of those licenses are more permissive than others.
What this means is that, while all provide in some way for open source software, they vary in the amount of protection they offer, the obligations they place on other developers who use the code, and how attribution should be handled. 

OpenVoiceOS has chosen, as [standard practice](https://openvoiceos.github.io/community-docs/license/), to license our software under the more permissive [Apache 2.0 license](https://www.apache.org/licenses/LICENSE-2.0) or the extremely permissive MIT license. 
We also make occasional use of the BSD license family. Permissive licenses allow users to modify and distribute the software with minimal restrictions. 

This approach contrasts with copyleft licenses, which require that any modifications or derivative works be released under similar terms. 

By allowing developers to use and modify our software freely, OpenVoiceOS hopes to attract a broad range of contributors who can help improve the platform and develop new applications.

## Why not copyleft?

OpenVoiceOS has chosen permissive licenses for a number of reasons, among which are the perceived drawbacks of copyleft. 

In our case, the team wanted to encourage widespread adoption and use of their software, without imposing significant restrictions on developers and businesses. 
While few copyleft licenses prohibit commercial activity, the obligation to pay code forward can be limiting in practice, and while the severity of this problem depends on the nature of the software, it's enough to deter many business-minded developers. 

**I don't want to deter anybody.**

Another factor that influenced the decision to avoid the GPL, a copyleft license, was the complexity of its terms and conditions. 
GPL is a legal document that is widely interpreted, and its requirements can be difficult to navigate for non-experts. 
By choosing simpler and more permissive licenses, OpenVoiceOS aimed to make it easier for others to understand and comply with licensing requirements.

A related license, also avoided here, is the LGPL. It has been popular for libraries, or code that helps other code. 
In lay terms, it was designed so that you could write a program *using* the licensed code as if it were permissively licensed; if you decided to *change* the licensed code, the changed code, and only that code, remains copyleft. 
My problem with the LGPL is simply that it uses terminology specific to the wrong technology. 
If we were a C/C++ shop, it might be a valuable tool in our arsenal, but as a mostly Python shop, [we aren't sure its language applies to us](https://softwareengineering.stackexchange.com/questions/119436/what-does-gpl-with-classpath-exception-mean-in-practice/326325#326325).

One of the problems with non-permissive licenses is that when a company cannot fully control how they share their code, they either do not use the software, or instead try hard to "hijack" the project by political maneuvering. 
Permissive licenses, such as the BSD or MIT licenses, allow the company to do whatever they want, and it does not become a part of their interest to hijack the upstream project or directly influence the way it is going. 
Companies who benefit from the permissive license often contribute code back to the project, because it is in their interest to have their contributions accepted and maintained upstream. 

This is not merely my position, but my ongoing experience, as we have routinely exchanged code in both directions with upstream and downstream entities.

Focusing on protecting the software from proprietary use does not align with the broader goal of benefiting the user and the open-source community. 
In many cases, proprietary products will develop their in-house solutions if they can't use open-source software. 
This doesn't serve the interests of the broader community and can lead to political maneuvering rather than genuine collaboration.

## How does this affect me?

What all of this means for developers is that they do not have to worry as much about compliance or how the software can be used. 
In addition, contributions made by those developers can more easily be integrated back into the original project. 

All together, this creates a symbiotic relationship that enhances the development process for everyone. 

OpenVoiceOS is meant to be a project for everyone, by everyone. 
We have worked to ensure this is the standard from top to bottom, and will continue that mission as we grow and change. 

A strong community is foundational to a healthy open source project, so I encourage you to get involved. 

Come chat with us on our [Matrix channels](https://matrix.to/#/!XFpdtmgyCoPDxOMPpH:matrix.org?via=matrix.org), and check out our [GitHub page](https://github.com/OpenVoiceOS)!