24202408100029
Status: #idea
Tags:

# Interface Philosophy
The principle of an interface based structure is quite simple. *Your managers / handlers shouldn't care about how a class is implemented!*

This is to say that, say you have a simple manager class for a brew: 

```java
public class BrewManager {  
	private static BrewManager instance;  
  
	public static BrewManager getInstance(){  
		if(instance == null){  
			instance = new BrewManager();  
		}  
	return instance;  
	}  
  
	private Map<UUID, Brew> brews;  
  
	private BrewManager(){  
		this.brews = new HashMap<>();  
	}  
  
	public void registerBrew(Brew brew){  
		this.brews.put(brew.getBrewId(),brew);  
	}  
  
	public void unregisterBrew(UUID brewId){  
		this.brews.remove(brewId);  
	}  
	public void activateBrew(Player player,UUID brewId){  
		brews.get(brewId).applyEffect(player.getPlayerId()) 
	}
}
```
Would you actually care *how* a "Brew" applies its effects with the "applyEffect" method? 
Would you care *how* a Brew gets its id? 
No, of course you wouldn't. You only care that its guaranteed to have a method that does this.

Lets now assume you had 2 different implementations of the "Brew" interface... would it matter which one was registered? No... because they are both Brews. 
Would you care if you used one type of Brew (Say one based on config stuff) or one based on some cool future app? No... both would have the "Brew" interface. 

So here is the semi-radical, but industry standard (and in turn for a plugin as complex as Brewery, the standard I propose).

*All Managers, Handlers, Listeners, Commands etc should only use the interfaces as the Type, even if what you are making is hard coded*

e.g: If you had a "ImplementedBrew", which implements the Brew interface, that could be constructed... nothing stops you doing this.
```java
Brew brew = new ImplementedBrew();
brew.getBrewName();
brew.getBrewType();
```

Think of how powerful this is? Imagine this was the start of a *200 line piece of code that uses "brew" dozens , if not 50+ times...*

Now imagine we realise we don't want to use the ImplementedBrew anymore, and build a whole new class called "NewImplementedBrew"

e.g: 
```java
Brew brew = new NewImplementedBrew();
brew.getBrewName();
brew.getBrewType();
```

*Note that code still works as the NewImplementedBrew instance is still an instance of "Brew".*
This is incredibly powerful as it means you could have 100's of lines of code that *does not need editing, even if you fundamentally change how brews work entirely*.

I hope this enough to explain the philosophy of the Interface based approach.

In future I think it'd be worth making some[[Interface Best Practices| best practices]] on how to create good interfaces. 





# References