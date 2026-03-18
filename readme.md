<mxfile>
  <diagram name="Aprovisionamiento Yealink Zoom">
    <mxGraphModel dx="1000" dy="600" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>

        <mxCell id="telefono" value="Teléfono Yealink" style="shape=rectangle;fillColor=#dae8fc;" vertex="1" parent="1">
          <mxGeometry x="50" y="200" width="140" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="dhcp" value="Servidor DHCP" style="shape=rectangle;fillColor=#d5e8d4;" vertex="1" parent="1">
          <mxGeometry x="250" y="50" width="140" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="fw" value="Firewall" style="shape=rectangle;fillColor=#f8cecc;" vertex="1" parent="1">
          <mxGeometry x="250" y="200" width="140" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="rps" value="Servidor RPS Yealink" style="shape=rectangle;fillColor=#fff2cc;" vertex="1" parent="1">
          <mxGeometry x="500" y="50" width="180" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="zoomprov" value="Servidor Zoom (Provisionamiento)" style="shape=rectangle;fillColor=#e1d5e7;" vertex="1" parent="1">
          <mxGeometry x="500" y="200" width="200" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="proxy" value="Proxy Zoom" style="shape=rectangle;fillColor=#e1d5e7;" vertex="1" parent="1">
          <mxGeometry x="750" y="200" width="140" height="60" as="geometry"/>
        </mxCell>

        <!-- Conexiones -->
        <mxCell id="e1" style="endArrow=block;" edge="1" parent="1" source="telefono" target="dhcp">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="e2" style="endArrow=block;" edge="1" parent="1" source="dhcp" target="telefono">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="e3" style="endArrow=block;" edge="1" parent="1" source="telefono" target="fw">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="e4" style="endArrow=block;" edge="1" parent="1" source="fw" target="rps">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="e5" style="endArrow=block;" edge="1" parent="1" source="rps" target="telefono">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="e6" style="endArrow=block;" edge="1" parent="1" source="telefono" target="zoomprov">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="e7" style="endArrow=block;" edge="1" parent="1" source="zoomprov" target="telefono">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="e8" style="endArrow=block;" edge="1" parent="1" source="telefono" target="proxy">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
