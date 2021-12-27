FROM node:14.18.0-alpine

WORKDIR /usr/src/app/loadmill
RUN npm i loadmill 

CMD ["sh", "-c", "./node_modules/loadmill/bin/loadmill ${TP_ID} --test-plan -vw -t ${TOKEN} --report --colors --additional-description \" build ${BUILD_NUMBER}\" "]
