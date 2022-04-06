# DRY > WET
## Only in software development though ;P

DRY code is a lot more readable and compact than WET code. And it's even more scalable! The best example is when you want to create a navbar component
Please note that this is given in the example of a React application :)

Take this code for example:

```
<div
  style={{
    display: "flex",
    flexDirection: "row",
    flexWrap: "nowrap ",
    gap: "10px",
  }}
>
  <h3
    className={
      splitLocation[1] === "Spotlight"
        ? "header-links-selected "
        : "header-links"
    }
    onClick={() => {
      history.push("/Spotlight");
    }}
  >
    Spotlight
  </h3>
  <h3
    className={
      splitLocation[1] === "Awards" ? "header-links-selected " : "header-links"
    }
    onClick={() => {
      history.push("/Awards");
    }}
  >
    Awards
  </h3>
  <h3
    className={
      splitLocation[1] === "Rewards" ? "header-links-selected " : "header-links"
    }
    onClick={() => {
      history.push("/Rewards");
    }}
  >
    Rewards
  </h3>
  <h3
    className={
      splitLocation[1] === "Incentives"
        ? "header-links-selected "
        : "header-links"
    }
    onClick={() => {
      history.push("/Incentives");
    }}
  >
    Incentives
  </h3>
  <h3
    className={
      splitLocation[1] === "Learning"
        ? "header-links-selected "
        : "header-links"
    }
    onClick={() => {
      history.push("/Learning");
    }}
  >
    Learning
  </h3>
</div>;
```

This dev really liked to write code. You can refactor this piece of code by using a simple object in JavaScript. The object can then contain key-value pairs of the UI you want to render to the user. Simply use the Object.keys() operator and then .map over each key to render theUI:
```
const PAGES = {
  Spotlight: "/Spotlight",
  Awards: "/Awards",
  Rewards: "/Rewards",
  Incentives: "/Incentives",
  Learning: "/Learning",
};


const renderRightLinks = () => {
  return (
    <div
      style={{
        display: "flex",
        flexDirection: "row",
        flexWrap: "nowrap ",
        gap: "10px",
      }}
    >
      {Object.keys(PAGES).map((key) => {
        return (
          <h3 key={key}
            className=
            {`mb-0 ${
              location.pathname.includes(PAGES[key])
                ? "header-links-selected"
                : "header-links"
            }
              `}
            onClick=
            {() => {
              history.push(PAGES[key]);
            }}
           >
            {key}
          </h3>
        );
      })}
    </div>
  );
};
```
Then wherever you want to render this UI component, you simple call the render method inside of the 'return' of your JSX component:
```
{renderRightLinks()}
```
And this is only on 5 elements! ^-^
