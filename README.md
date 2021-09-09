# assignment2-Kandimalla
# GopiKrishna Kandimalla

###### Goa is the best place to visit in INDIA

Goa is popularly known as the Pearl of the orient and tourist paradise.**Apart from attracting tourists from all over India,it also attracts tourists of foreign background**.During the months of November,December and January Goa is heavily crowded.**There are more than 35 beaches in Goa**,each one is known for its own distinctiveness.The beach is the best attraction of Goa.It was so much fun to be at the beach.

---
## Travel Instructions

1. This travel guide to Goa will list out all the practical travel tips to the Coastal state of West India, and the country’s most beloved beach destination.
2. Each time, I visit, Goa opens a new chapter from past, while siting glorious nature by side.
3. One and only option to reach goa is by Flight.
    1. Before your trip you need to apply and obtain your visa (or)
    2. You should be an Indo-American.
4. Quick & useful Information about Goa travel:
    1. Language spoken: Konkoni, Marathi. Largely understood- English and Hindi.
    2. Famous for Beautiful beaches, water-sports, night-markets, sea food, yoga, nightlife
    3. Safer place to travel to for solo women in India
    4. It is a tiny state. Prosperous and with higher literacy rate. One of the leading tourist destinations in India.
5. You can also hire bikes, cars by depositing your licence. Do not forget to get a photo of the license which will can be further used at police check points on the road if any.
6. Where to stay in Goa:
    1. Staying at Baga/Calangute
    2. Staying at Arambol/Ashwem (extreme North Goa).
    3. Staying at South Goa.

### Must-carry things on a trip to Goa.

* Mirrored sunglasses.
    * Protects eyes from harh UV rays in beach.
* Rubber footwear.
    * Comfortable to walk on sandy beaches.
* Dress.
    * Wear them for evening dinner and beach parties.
* Umbrella
    * Just in case it rains or if you need some shelter from the sun.
* Sarong / Multi drape coverups.
    * Makes your bag light

 Link to AboutMe: <br>
[AboutMe](https://github.com/Gopikrishna29/assignment2-Kandimalla/blob/main/AboutMe.md)

---

## Food Menu

| Food | Place | Cost |
| ---| ---| ---: |
| Crispy Chicken Sandwich | McDonald's | $5.16 |
| Big Mac Meal | McDonald's | $10.42 |
| Classic Chicken Sandwich Box | KFC | $11 |
| Famous Bowl | KFC | $5.99 |

---
## Pithy Quotes

> “If I had a flower for every time I thought of you, I could walk in my garden forever.”<br>
  &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; – *Saivivek Reddy*

> “I look at you and see the rest of my life in front of my eyes.” <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; – *Jawahar Reddy*

 ---

 > Consider two sets A and B of points on a plane. Minkowski sum A+B is defined as a+b|a∈A,b∈B. Here we will consider the case when A and B consist of convex polygons P and Q with their interiors. Throughout this article we will identify polygons with ordered sequences of their vertices, so that notation like |P| or Pi makes sense. It turns out that the sum of convex polygons P and Q is a convex polygon with at most |P|+|Q| vertices.

 Here is the link: <https://cp-algorithms.com/geometry/minkowski.html>

 Here is the code for `Minkowski sum of convex polygons`

 ```
 struct pt{
    long long x, y;
    pt operator + (const pt & p) const {
        return pt{x + p.x, y + p.y};
    }
    pt operator - (const pt & p) const {
        return pt{x - p.x, y - p.y};
    }
    long long cross(const pt & p) const {
        return x * p.y - y * p.x;
    }
};

void reorder_polygon(vector<pt> & P){
    size_t pos = 0;
    for(size_t i = 1; i < P.size(); i++){
        if(P[i].y < P[pos].y || (P[i].y == P[pos].y && P[i].x < P[pos].x))
            pos = i;
    }
    rotate(P.begin(), P.begin() + pos, P.end());
}

vector<pt> minkowski(vector<pt> P, vector<pt> Q){
    // the first vertex must be the lowest
    reorder_polygon(P);
    reorder_polygon(Q);
    // we must ensure cyclic indexing
    P.push_back(P[0]);
    P.push_back(P[1]);
    Q.push_back(Q[0]);
    Q.push_back(Q[1]);
    // main part
    vector<pt> result;
    size_t i = 0, j = 0;
    while(i < P.size() - 2 || j < Q.size() - 2){
        result.push_back(P[i] + Q[j]);
        auto cross = (P[i + 1] - P[i]).cross(Q[j + 1] - Q[j]);
        if(cross >= 0)
            ++i;
        if(cross <= 0)
            ++j;
    }
    return result;
}

```
Here is the link for reference: <https://cp-algorithms.com/geometry/minkowski.html>
