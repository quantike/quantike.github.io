---
layout: post
title:  "You don't read enough code."
---

# You don't read enough code.

> This post is inspired by the xweet from [@kuberdenis](https://x.com/kuberdenis) titled "You are not a software engineer."[^1] This post serves as one way to overcome the challenge he describes.

[^1]: [You are note a software engineer.](https://x.com/i/bookmarks?post_id=1869383856723464402) 

If you’re reading this, you probably know how to code at some level. You also probably don't read enough code.

If you are learning to program, read more code. If you are learning a new language or framework, read more code. If you’re writing your own database, read more code.

Almost everything we do in software is not new. The sum product of the business might be new to the market, but it’s powered by databases and HTTP just like every other start up. 

This is to your advantage. 

Almost everything has been done before. Your job is to read it, understand it, and iterate on it. 
### Grasp the high level concepts
Oftentimes, I am reading code thinking “what a terrible name for that class”, only to later realize it’s the only name that makes sense as my understanding of the repository grows. Here's how I like to read code:

1. Find the “Entry Point”: Start from the entry point (maybe a `server.rs` or a `main.py`) of the code and work your way down through the various code paths.
2. Pick a data structure that is fundamental to the repository and go read every place it is used (code navigation tools can help with this).
3. Read the Pull Request history. This is where you can see the intentionality and decision making process take place. 

The higher-level reasoning develops as you build understanding with the code base. Design decisions reveal themselves, and so do the short-comings. 

To better understand short-comings, go read the Issues.

### Read Efficiently
Use code navigation tools:

- Check the Github side bar for their "Symbols" section. Use it to navigate. Click on the struct you are looking at and go find how it's implemented and where it is used.
- When reading code in an IDE get familiar with "go to definition". Make a hot-key for it ([neovim](https://github.com/quantike/dotfiles), btw). 

Use code understanding tools:

- RTFM![^2]
- I find that AI tools work best at a narrowly scoped coding problem

[^2]: [RTFM](https://en.wikipedia.org/wiki/RTFM#:~:text=RTFM%20is%20an%20initialism%20and,forum%2C%20software%20documentation%20or%20FAQ.)

Example: "What does the `|= 1 << i` syntax do in this `.hash()` function for my locality-sensitive hashing implementation?"[^3]
```rust
fn hash(&self, vector: &Array1<f64>) -> u64 {
	let mut hash_value: u64 = 0;

	for (i, hyperplane) in self.hyperplanes.iter().enumerate() {
		let dot_product = vector.dot(hyperplane);
		if dot_product > 0.0 {
			hash_value |= 1 << i;
		}
	}

	hash_value
}
```

[^3]: [Locality sensitive hashing](https://en.wikipedia.org/wiki/Locality-sensitive_hashing) 

### The habits you need to change
Be a voracious reader. Read the deploy scripts. Read the config files. Read the Dockerfiles. You should read every piece of the code in some capacity (maybe not the lockfiles though, unless you’re working on [bun](https://github.com/oven-sh/bun) or [uv](https://github.com/astral-sh/uv))

Challenge yourself to understand the tools you use. Very few Python developers (at least the ones I know) know how their favorite tools work under the hood. Next time you reach for [fastapi](https://github.com/fastapi/fastapi), spend some time reading the code base.

Think about your own implementations. Take an arbitrary entry point, like a post endpoint and ask yourself how you would do it, then go see how they did it. 

Read more code. 
