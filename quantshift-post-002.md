# When Options Have Slope: A Visual Guide to Call and Put Derivatives

*“Wait... you can take the derivative of a call option?”*

Turns out, not only **can you**, but doing so reveals the logic behind how option payoffs behave — and why they behave that way.

In this notebook, we’ll explore the **derivatives of the basic call and put payoff functions** — not using stochastic models or PDEs, but just pure, visual calculus.

This is part of my ongoing **Pencils & Python** series, where I document math and finance concepts as I work through foundational material in quant finance.


## What Are Call and Put Options?

Before we dive into slopes and calculus, let’s briefly recap what these options actually are:

- A **call option** gives the holder the *right* (but not the obligation) to **buy** an asset at a specified price (called the **strike price**) before or at expiration.

Think of it like this: You have the right to buy a stock at 100 dollars even when its price rises to 120 dollars, letting you profit the difference.

- A **put option** gives the holder the right to **sell** an asset at the strike price.

  If the market price drops to 80 dollars, but your put lets you sell at 100 dollars, you just profited 20 dollars.

In this post, we’re going to look at their **payoff functions** — the formulas that tell us how much these options are worth at expiration — and see how we can understand their behavior using basic calculus.


## What Do These Options *Actually* Pay You?

Now, let’s talk about what these things are worth when they *really matter* — at expiration.

A **call option** is like locking in a deal to **buy low** in case the market goes high. You’re not obligated to use it — but if it’s a good deal, you’ll take it.

The formula for the value of a call at expiration is:

$$
\text{Call Payoff} = \max(S_T - K, 0)
$$

Basically:
> “If the stock price \( S_T \) ends up above the strike price \( K \), I pocket the difference. If not? Meh. I walk away.”

A **put option** is the opposite — it lets you **sell high**, even if the market tanks. It’s like having insurance on your shares.

$$
\text{Put Payoff} = \max(K - S_T, 0)
$$

So if the stock crashes? Your put gets more valuable. If the stock holds strong? The put is worth nothing — but that’s okay, you didn’t need the safety net.

---

In Python, we can express both payoffs using NumPy like this:



## So... What Happens When We Look at the Slope?

Okay, so we’ve got these payoff functions — clean, piecewise, kind of like financial “if-then” statements.

But here’s the question that kicked off this whole notebook for me:

> What happens if we take the **derivative** of these payoffs?

Sounds simple enough, right? But what we’re really asking is:

- *How fast does the value of the option change?*
- *At what point does the option “come alive”?*
- *And what does that slope actually tell us about market behavior?*

That’s where this gets fun — because we can use basic calculus to uncover the **behavioral turning point** baked into every option contract.

Let’s start by modeling those slopes.


## What These Slopes Actually Tell Us

Let’s decode what those slope values mean in plain English.

### 📈 For a **call option**:

- **Before the strike**:
  The option is worthless — no one wants to pay more than market price.
  → The slope is **0**. No change, no value.

- **After the strike**:
  The option gains a dollar for every dollar increase in stock price.
  → The slope jumps to **1**. It's fully “in the money” now.

### 📉 For a **put option**:

- **Before the strike**:
  You’re in the money — the lower the stock goes, the more valuable the option.
  → The slope is **–1**. Price drops, payoff rises.

- **After the strike**:
  The put becomes worthless — you wouldn’t exercise the right to sell high if the market is already high.
  → The slope flattens to **0**.

---

So even though the payoff functions have a **“kink”** at the strike price (meaning they’re not differentiable exactly at that point), they still have **clear, simple slopes everywhere else**.

And now… let’s see that behavior in action with a plot.


## Seeing the Slopes in Action

We used Python and a couple of popular libraries — **NumPy** for math and **Matplotlib** for plotting — to bring these payoff functions to life.

Rather than walk through all the code, you can explore my GitHub repository (Link at end of this post).  Here’s what we plotted:

- **Call and put option payoffs** side-by-side
- Their **first derivatives** — showing how the slope changes before and after the strike

Here’s the result:


### Placeholder for image

## Wrapping It All Together

Options may seem like abstract financial instruments — but when you break them down into their **payoff functions**, and then zoom in on their **slopes**, you start to see the logic underneath:

- A **call option** doesn’t care what the stock is doing until it crosses the strike — then it springs to life, gaining dollar-for-dollar.
- A **put option** is the opposite: full of value when the stock is low, but loses its edge once the price rises.

And here’s the cool part:
This isn't just math. It's **behavior**.
These slopes — these simple little pieces of calculus — **tell the story of incentives**, of risk, of leverage. They're the fingerprints of how options respond to the market.

---

I hope this post gave you a clearer, more intuitive understanding of how options behave — and how calculus helps us decode them.

Want to dig deeper? The full code and notebook are available here:
👉 [GitHub: quantshift_post_002](https://github.com/Pencils-and-Python/quantshift-post-002)

This post is part of my **Pencils & Python** series — documenting what I’m learning as I explore the intersection of **math, modeling, and markets**.

In upcoming posts, I’ll be working through calculus, linear algebra, and stochastic modeling techniques as I build toward more advanced topics in option pricing and algorithmic trading.

Thanks for reading! 🚀
