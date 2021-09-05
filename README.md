# Likhitha Gopi
### My favorite place in the world is venice<br>
**Venice** is also known as the “**City of Canals**,” “**The Floating City**,” and “**Serenissima**.”  It is one of Italy's most picturesque cities.<br>Venice is basically built on wood and water.
****
## Maryville to Venice
1. Maryville to Kansas International Airport(MCI)
    1. Travel by Car
2. MCI to VCE(Venice, Italy)
    1. Direct Flight
    2. Connecting Flight (Maryville to Los Angeles and Los Angeles to Venice)
## List of items that should be brought to your favorite place for maximum enjoyment
* Umbrella
* Camera
* Sun Glasses
* Paper Boats

[Click here to see About Me](./AboutMe.md)
****
## Food And Drinks
The below are the list of Food/drinks I would recommed to try !!
| Item | Location | Cost |
|------|----------|------|
| Chiken Supreme Pizza | Pizza Hut | $10 |
| CheeseBurger | McDonalds | $2 |
| Hot Choclate | StarBucks | $3.45 |
| Choclate Milkshake | Mooyah | $4 |

****
## Pithy Quotes
> "Feed your Faith and starve your doubts."  *-Billy Cox*

> "Turn your scars into Stars." *-Robert H. Schuller*

****

>The convex hull of a set of points is the smallest convex polygon that surrounds the entire set, and has a number of practical applications. An efficient method that is often used in challenges is the Graham scan [2], which requires a sort by angle. This isn’t as easy as it looks at first, since computing the actual angles is expensive and introduces problems with numeric error. A simpler yet equally efficient algorithm is due to Andrew 

[Quick-link for the source](https://massivealgorithms.blogspot.com/2019/01/convex-hull-sweep-line.html?m=0)

```
struct pt {
    double x, y;
};

bool cmp(pt a, pt b) {
    return a.x < b.x || (a.x == b.x && a.y < b.y);
}

bool cw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) < 0;
}

bool ccw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) > 0;
}

void convex_hull(vector<pt>& a) {
    if (a.size() == 1)
        return;

    sort(a.begin(), a.end(), &cmp);
    pt p1 = a[0], p2 = a.back();
    vector<pt> up, down;
    up.push_back(p1);
    down.push_back(p1);
    for (int i = 1; i < (int)a.size(); i++) {
        if (i == a.size() - 1 || cw(p1, a[i], p2)) {
            while (up.size() >= 2 && !cw(up[up.size()-2], up[up.size()-1], a[i]))
                up.pop_back();
            up.push_back(a[i]);
        }
        if (i == a.size() - 1 || ccw(p1, a[i], p2)) {
            while(down.size() >= 2 && !ccw(down[down.size()-2], down[down.size()-1], a[i]))
                down.pop_back();
            down.push_back(a[i]);
        }
    }

    a.clear();
    for (int i = 0; i < (int)up.size(); i++)
        a.push_back(up[i]);
    for (int i = down.size() - 2; i > 0; i--)
        a.push_back(down[i]);
}
```
[Quick-link for the code source](https://cp-algorithms.com/geometry/grahams-scan-convex-hull.html)
