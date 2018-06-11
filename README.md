# cleaning-zone-data
getting rid of all those ugly values!

%cleaning zone data


%call files
filename = "SpanishPortuguese_400kV_Location_PowerGrid1";
generation = "Generación";
sheetnodos = "Nodos-Localizacion";

values = xlsread(filename, sheetnodos, "F2:R305");
node_id = (1:304)';

%rows and columns of values table
[m,n] = size(values);

%checks for each column, each number is not NAN (is a num)
node_zone = zeros(m,1);
for i = 1:n
  for j = 1:m
    if ~isnan(values(j,i)) %if it´s a number, record the zone
      node_zone(j) = i;
    else
        node_zone(j,i) = 0;
    end 
  end
end


node_pairing = [node_id, node_zone];
