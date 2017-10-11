#jq
#manual https://stedolan.github.io/jq/manual/

sudo apt-get install jq

curl 'some api' | jq '.[0]'

wget 'a  geojson file'



cat data_requests_2017/teska/parking_lot.geojson | jq '.' | less

cat data_requests_2017/teska/parking_lot.geojson | jq '.features' | less

cat data_requests_2017/teska/parking_lot.geojson | jq '.features[0]' | less

cat data_requests_2017/teska/parking_lot.geojson | jq '.features[0].properties | less

cat data_requests_2017/teska/parking_lot.geojson | jq '.features[].properties.parkinglot_poly_id' | less

#another way to do the same thing but change the name
cat data_requests_2017/teska/parking_lot.geojson | jq '.features[] | {ID: .properties.parkinglot_poly_id}' | less

cat data_requests_2017/teska/parking_lot.geojson | jq '.features[] | {ID: .properties.parkinglot_poly_id, LotNumber: .properties.lot}' | less

#with geometry
cat data_requests_2017/teska/parking_lot.geojson | jq '.features[0] | {ID: .properties.parkinglot_poly_id, LotNumber: .properties.lot, geom: .geometry,}' | less

# select specific items
cat data_requests_2017/teska/parking_lot.geojson | jq '.features[].properties | select(.lot_part_type | contains("road"))' | less

cat data_requests_2017/teska/parking_lot.geojson | jq '.features[].properties | select(.parkinglot_poly_id==224)' | less

#find the number of items in a file
cat data_requests_2017/teska/parking_lot.geojson | jq '.[] | type,length' | less


# 