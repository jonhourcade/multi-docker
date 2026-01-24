# giving the output image an alias we can reference in a later stage
from node:lts-alpine as builder 

workdir /app

copy ./package.json ./

run npm install

copy . .

# note: run, not cmd
# run is used during the build process, cmd is used when the container is started
run npm run build


from nginx

expose 3000

# first part is the location of our custom config file
# second part is the location nginx expects its config files to be
copy ./nginx/default.conf /etc/nginx/conf.d/default.conf

# /app/build is where our react app is built to in the previous stage
# /usr/share/nginx/html is where nginx serves files from
copy --from=builder /app/build /usr/share/nginx/html