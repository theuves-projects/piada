#!/usr/bin/env node
"use strict";

// piada | matheus alves
// https://github.com/theuves/piada

var http = require("http");
var iconv = require("iconv-lite");

http.request({
  host: "aspiadas.com",
  path: "/randomjoke.php"
}, function (response) {
  if (response.statusCode === 200) {
    response.pipe(iconv.decodeStream("ISO-8859-1"))
      .collect(function (error, body) {
      if (error) {
        console.error("Erro!");
        process.exit(1);
      } else {
        console.log(body
          .split("</table><p>")[1]
          .split(/<\/p><div\salign="center">/)[0]
          .replace(/\n?<br\s\/>/g, ""));
      }
    });
  } else {
    console.error("Serviço indisponível.");
    process.exit(1);
  }
}).on("error", function () {
  console.error("Serviço indisponível.");
  process.exit(1);
}).end();
