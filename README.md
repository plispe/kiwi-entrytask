# Entry task for the Kiwi.com Weekend in the Cloud
[![CircleCI](https://circleci.com/gh/plispe/kiwi-entrytask/tree/master.svg?style=svg&circle-token=0b4f358e9943f9468787e87bbcbd5f32f27438b5)](https://circleci.com/gh/plispe/kiwi-entrytask/tree/master)
[![](https://dockerbuildbadges.quelltext.eu/status.svg?organization=petrpliska&repository=kiwi-entrytask)](https://hub.docker.com/r/petrpliska/kiwi-entrytask/builds/)

*Requirements*

- A simple html site, with the title "I want to attend the Kiwi.com Weekend in the Cloud"

- Use Nginx as your web server

  - BONUS: use SSL

    - Hint: use Let's Encrypt

    - https://letsencrypt.org/docs/certificates-for-localhost/

- Use Docker Hub to build and share your image

*Notes*

- I use alpine Linux based Nginx image because I like to keep my docker images as small as possible
- I embed self-signed SSL certificate on build into docker image because Let's Encrypt can’t provide certificates for “localhost”. Personally, I would never embed SSL certificates into docker image(the only exception would be an image for development purposes). I did it only to meet your BONUS "use SSL" requirement
- I also configured Nginx for redirects from HTTP to HTTPS
- I wrote tests for docker images using [Goss](https://github.com/aelsabbahy/goss) testing tool. Tests run on every git push in [CircleCI](https://circleci.com/gh/plispe/kiwi-entrytask)
- I configured docker hub auto build only for git tags. Git push will trigger image build and tests in CircleCI and git push tag triggers Docker Hub build. I used Docker Hub build only to fulfill your requirements because build images with CicrcleCI would be a way better option.