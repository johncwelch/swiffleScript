# swiffleScript
Defining a replacement for AppleScript

(dear god I hate markdown, it'a such a fucking clown show)

So given Apple, it has become obvious they have no interest in supporting any form of user automation that isn't 100% controlled by devs, i.e. Shortcuts. This is not to say Shortcuts are bad, they're a great paradigm for a lot of things. But if you as just a person want to do a thing Shortcuts don't allow for, you can't. It's literally impossible, again, by design. If the dev doesn't feel like, or doesn't see any value in adding the functionality you want to an application, you're shit out of luck. By design.  

However, since it's doubtful the underlying mechanisms that allow Shortcuts to work, including the Apple Event mechanism, will go away, then there's perhaps a way to not lose what things likke AppleScript, and PowerShell on windows gives us. Yes, it would be nice if Apple were to build an OS-wide automation framework into macOS, (or i(Pad)OS, but you're more likely to get a free million dollars from Apple than see that happen. The last time that existed was Mac OS 9. Yeah, even the great STEEEEVE didn't care. So accept reality.  

Also, I, obviously, have nothing against AppleScript. It's an amazing tool a far better language than people want it to be, whose greatest sin is not being C or JavaScript. The problem is, there's nothing that allows you to progress from AppleScript to Swift. There was, for a while, AppleScript Objective-C, ASOC, which was a great bridge, but ObjC is on the way out, so there's no bridge to get one into Swift, or SwiftUI the way ASOC did to help one move from AppleScript to ObjectiveC.  

This is a really important feature, it's one of the biggest advantages of Powershell, the fact you can ease into full C#/.NET development from PowerShell. PowerShell syntax is remarkably similar to C#/.NET, so what you learn in PS is applicable in C#. Huge. You can even incorporate the .NET frameworks directly into a powershell script. By creating PowerShell in that manner, Microsoft made it easier to escape the limitations of PowerShell, and allowed PowerShell to not have to morph into C#.  

So with this in mind, I think, even as a long time AppleScript fan, user, and developer, it is time to replace AppleScript with a scripting language that will provide an on-ramp into Swift/SwiftUI, both in terms of syntactical similarity and the ability to import the various Swift frameworks in macOS. Note, *similar*, not *identical*, or as is said in the makeup world, "sisters, not twins". For example, function calls in powershell are very similar to C# function calls, but they are not identical. There's no public/private visibility requirement for PowerShell functions, nor is there a requirement for a return type. If you want to return a value in a powershell function, you use return \<value\> in the function and then use a variable when calling the function, i.e. $myVAR = myFunction()  

So with that in mind, swiffleScript (a really bad combination of swift and AppleScript) will not seek to be identical to swift. Obviousness, ease of use, and consistency are it's prime requirements. Will it multithread? Dear god no, why would you do that to people, nor should it need to. If you want threading, you have that. In Swift. Sisters, not twins. Also, if anyone wants to contribute, that's great. But this is not a committee. It is at best a benevolent dictatorship. Someone has to be in charge, so like N*SYNC says, "It's gonna be me". If that bothers you, you are free to not contribute, no harm, no foul.

# Principles

1. The overriding reqirements of swiffleScript shall be Obviousness, Clarity, and Intuitivity. Keywords shall make it clear what the keyword is for and what it does. For example, there's no sense to why, in Swift, "let" is a constant and "var" is mutable. Why not use "const"? The world will never know (please, don't tell me, it's just going to be some elitest nonsense or the even dumber "let" has fewer letters than "const".) If the default Swift syntax is unclear, swiffleScript will depart from that.
2. With regards to the first principle, swiffleScript will be careful about where it departs and be clear about why. There has to be a reason to change something, like not using "let" for constants because it is dumb, but allow for constants via say, the powershell mechanism for Set-Variable, which has a -Options parameter that allows one to set a variable as a constant.
3. Where it doesn't damage the first principle, swiffleScript will allow for multiple ways to accomplish a basic, common task. Again, using PowerShell and vars, if you just want to make a variable that's a string, $var = "some text" creates a string variable named $var with "some text" as its value. If you want to make it a constant with a specified scope, then you would use Set-Variable -Name theVarName -Value "The var contents" -Option constant -Scope Global -Visibility Public. This allows for simplicity for the common case, while giving the scripter the ability to be specific where needed.
4. I'm very much leaning towards swiffleScript being case-insensitve. Case sensitivity is this silly holdover from when 4K was a lot of ram, and well, Unix and C have it so EVERYONE MUST. Nonsense. case-insensitivity removes the issue where people are seeing bugs because they used theVar instead of thevar. It makes it harder to code, harder to debug, I've yet, in 30 years, seen a single cogent argument for case sensitivity other than "that's the way we've always done it."
5. swiffleScript will not have all the features of Swift. As stated earlier, it will not thread. There will be other differences, such as avoiding the SwiftUI frustration of "the order you have statements in the code may not have anything to do with when they execute and oh won't that be FUN for the new person!!!" When incorporating external frameworks, that will be a different case, but for now, outside of things like functions, line 9 executes before line 10
6. swiffleScript will not do the PowerShell thing where the script looks like it's finished when it really hasn't and you learn quick to use -Wait -NoNewWindow wherever it exists. That is a thing I call "lying" and I dislike it *intensely*. If the only way to achieve a specific bit of funcitonality is to lie, probably won't be in swiffleScript.
7. swiffleScript shall be interpreted. There should be a way to convert it to a conventional compiled executable, but within itself, swiffleScript shall be interpreted
8. Ideally, the debugger for swiffleScript will work like Late Nite Software's Script Debugger's. No having to set breakpoints, or what have you. Enable the debugger, click step through and off thou goest. It's remarkably intuitive and I feel sad for folks who have never had a chance to experience a debugger that is both complete and easy to use. Breakpoints will exist, obviously, they are incredibly useful. But you shouldn't have to set one at line one just to slowly step through a script.
9. this left intentionally blank
10. As is this one

more to come, but I have to poop.
