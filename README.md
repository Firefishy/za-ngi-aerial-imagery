# za-ngi-aerial-imagery
Guide on processing NGI Aerial Imagery
# Commands (Draft)
```
open 3318CD_25_2014_699_RGB_RECT.tif
docker run -it -v $(pwd):/data geodata/gdal:2.1.1 gdalinfo 3318CD_25_2014_699_RGB_RECT.tif
docker run -it -v $(pwd):/data geodata/gdal:2.1.1 gdalbuildvrt --help
open http://www.gdal.org/gdalbuildvrt.html
docker run -it -v $(pwd):/data geodata/gdal:2.1.1 gdalbuildvrt -resolution highest -addalpha -hidenodata data.vrt *.tif
docker run -it -v $(pwd):/data geodata/gdal:2.1.1 gdalinfo data.vrt
docker run -it -v $(pwd):/data geodata/gdal:2.1.1 gdaladdo --help
open http://www.gdal.org/gdaladdo.html
docker run -it -v $(pwd):/data geodata/gdal:2.1.1 gdaladdo -ro --config COMPRESS DEFLATE --config COMPRESS_OVERVIEW DEFLATE --config ZLEVEL 9 --config BIGTIFF_OVERVIEW IF_SAFER --config GDAL_TIFF_OVR_BLOCKSIZE 512 -r average data.vrt 4 16 64 256 1024 4096 16384
open data.vrt
```
