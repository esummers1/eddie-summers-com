---
date: 2019-03-01T18:00:00+00:00
title: "Google Hashcode"
summary: "Google HashCode is an annual world-wide team programming competition. I entered it with three friends as team Holy Guacamole in 2019 and 2020."
categories: ["Projects"]
splash: "/images/holy-guac.jpg"
---

*Team Holy Guacamole*

Google HashCode is an annual world-wide team programming competition. I entered it with three friends as team Holy Guacamole in 2019 and 2020.

The problem in 2019 was to arrange photo objects into slideshows which were most 'interesting', according to a certain algorithm. Our solution started at the basic level - composing slideshows of photos in the order they were recevied - and advanced to attempting to group photos with popular 'tags' nearer each other, as such groupings were worth more points.

We wrote our [solution in Typescript](https://github.com/Danjb1/google-hashcode-2019), which was compiled and run on Node. Afterwards, I [ported our application to Python](https://github.com/esummers1/hashcode19) and continued to work on it. Since Google provide several input files that have different characteristics, one strategy does not fit all - I designed the Python version to have a bank of strategies with which to group each set of photos, and to choose the most successful strategy for each input file to generate the output solution.

In 2020, the problem was harder, and revolved around scheduling the scanning of physical books in libraries with different collections. Again, we wrote our [solution(s) in TypeScript](https://github.com/esummers1/hashcode-2020) and ran them using Node. While we intended to apply the strategy-selection logic throughout, the problem this year was not easy to model, and we did not have enough time to build a local scoring engine.

In both cases, we finished in the top 30% of teams worldwide.
