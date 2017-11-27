---
title: Como criar uma forma usando um PathGeometry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31f77f0921bb018317834077f70e4623c47a4f7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="a75ef-102">Como criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="a75ef-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="a75ef-103">Este exemplo mostra como criar uma forma usando o <xref:System.Windows.Media.PathGeometry> classe.</span><span class="sxs-lookup"><span data-stu-id="a75ef-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="a75ef-104"><xref:System.Windows.Media.PathGeometry>objetos são compostos de um ou mais <xref:System.Windows.Media.PathFigure> objetos; cada <xref:System.Windows.Media.PathFigure> representa uma forma ou diferente "Figura".</span><span class="sxs-lookup"><span data-stu-id="a75ef-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="a75ef-105">Cada <xref:System.Windows.Media.PathFigure> é composto de um ou mais <xref:System.Windows.Media.PathSegment> objetos, cada um representando uma parte conectada da figura ou forma.</span><span class="sxs-lookup"><span data-stu-id="a75ef-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="a75ef-106">Tipos de segmento incluem <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, e <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="a75ef-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a75ef-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a75ef-107">Example</span></span>  
 <span data-ttu-id="a75ef-108">O exemplo a seguir usa um <xref:System.Windows.Media.PathGeometry> para criar um triângulo.</span><span class="sxs-lookup"><span data-stu-id="a75ef-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="a75ef-109">O <xref:System.Windows.Media.PathGeometry> é exibido usando um <xref:System.Windows.Shapes.Path> elemento.</span><span class="sxs-lookup"><span data-stu-id="a75ef-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="a75ef-110">A ilustração a seguir mostra a forma criada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="a75ef-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="a75ef-111">![Um PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="a75ef-111">![A PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="a75ef-112">Um triângulo criado com um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="a75ef-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="a75ef-113">O exemplo anterior mostrou como criar uma forma relativamente simples: um triângulo.</span><span class="sxs-lookup"><span data-stu-id="a75ef-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="a75ef-114">Um <xref:System.Windows.Media.PathGeometry> também pode ser usado para criar formas mais complexas, incluindo arcos e curvas.</span><span class="sxs-lookup"><span data-stu-id="a75ef-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="a75ef-115">Para obter exemplos, veja [Criar um arco elíptico](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [Criar uma curva de Bézier cúbica](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md) e [Criar uma curva de Bézier quadrática](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="a75ef-115">For examples, see [Create an Elliptical Arc](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="a75ef-116">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="a75ef-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75ef-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a75ef-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [<span data-ttu-id="a75ef-118">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="a75ef-118">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="a75ef-119">Exemplo de geometrias</span><span class="sxs-lookup"><span data-stu-id="a75ef-119">Geometries Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159989)