# cleaning-zone-data
getting rid of all those ugly values!


filename = "Spanish_Portuguese_400kV_Location_PowerGrid1";
generation = "Generación";
sheetnodos = "Nodos-Localizacion";

[values, zones] = xlsread(filename, sheetnodos, "F1:R305");
node_id = xlsread(filename, sheetnodos, "B2:B305");

[m,n] = size(values);


node_zone = zeros(m,1);
for i = 1:n
  for j = 1:m
    if ~isnan(values(i,j))
      node_zone = i;
    end
  end
end

node_pairing = [node_id, node_zone];
